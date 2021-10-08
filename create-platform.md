# Create Support for a new Platform

<!-- TODO: Add guidelines for what platforms will not be supported -->

## Write the extractor

### Guidelines for a extractor

It is best to make your extractor as light as possible. For this reason I would
recommend a rss-feed if the platform has one. Please additionally make only one
`GET`-request per subscription.

### Writing the extractor

#### Needed structs

You will need two structs you define in your new platform, one for the video 
and one for the subscription.

Your video struct will just hold some basic information about the video that 
can be queried, e.g. a playable url, the video title. It will have to implement
the `Video`-trait defined in `tf_core/src/definitions/video.rs`. The 
`Subscription`-type will be the subscription you define next.

The subscription structure will hold information about the channel, e.g. the 
name, and information that will be used to query the uploaded videos from the
channel. You will have to implement the `Subscription`-trait defined in 
`tf_core/src/definitions/subscription.rs`, the `Video`-type is the struct you 
defined before.

#### The extraction process

To extract videos from the subscription, you will need to implement the 
`GeneratorWithClient`-trait defined in `tf_core/src/definitions/generator.rs`.
The `Item`-type will be your video, the `Iterator`-type will depend on your 
implementation.


##### RSS

If you took the easy route of a rss-based extraction, you can use the tools 
defined in `tf_utils/src/rss/rss_extractor.rs`. You will basically just need to 
implement `RssExtractor` for your subscription to get the url of the rss feed
and overwrite the `WithName` as you will most likly not have the subscription
name when initializing the subscription.
Your video will need to implement `FromItemAndSub`, the generic variable `S` 
will be your defined subscription.

If your rss feed requires some tags not already defined in the rss structure, 
please edit `tf_utils/src/rss/structure.rs` to your liking.
If the tag has `:`, please replace it with `/` and also do so in 
`tf_utils/src/rss/rss_extractor.rs` similar to `media:` or `itune:`.

Please see the `Peertube`-platform for a example.

##### REST

If your platform does not have a rss-feed or using one is not practical, you 
will have to do most of the work manually, see the `Youtube`-platform as a 
example.

Please implement the REST-Client in a different crate if this is too complex
or use a already defined crate if available.

#### Thumbnails

You will most likly have thumbnails for your video. If these thumbnails are
`jpg`, `png` or any other in 
[this table](https://docs.rs/image/0.23.14/image/codecs/index.html#supported-formats)
supported platforms, you will just have to overwrite `thumbnail_url` for your 
video. As `webp` currently is only supported grayscale-only you will have to 
overwrite `convert_image` in your video, that will convert the image bytes to a
usable `DynamicImage`. For a example, see the `YTVideo` defined in 
`tf_platform_youtube/src/video.rs`.

## Integrate into `tf_join`

_Note_: Currently you will have to add your new platform to almost any file in 
the `t_join` crate. I currently do not know how this could be made easier, but 
it is currently mostly copy-and-paste.

The `tf_join` crate is split into a feature for every platform. Please add your
new platform with a new feature into the `Cargo.toml`.

In the `tf_join` crate you will find many comments starting with `--`, e.g.
`// -- Add new value here.`. At these comments you will need to copy-and-paste
the previous code-block, match-case or similar and edit it for your new 
platform. Most of the edits are very minor (e.g. a new field in a struct) and
some require more thinking (e.g. (de)serializing to csv).
Please do not forget `#[feature = "platform"]` before your code, and also update
the `join` example for testing.

## Integrating into `Tubefeeder`

In `Tubefeeder` you will have to change two files. 
In `subscription_adder.rs` you will need to change what entry boxes are 
visible when selecting your new platform (in the `view!`-macro, see the 
`Peertube` platform for a example), and how your subscription will be 
generated from the input values in the `add_subscription`-function.

In the `subscription_item.rs` you will need to change whether the name of the 
subscription should be updated when displayed (instead of displaying the id).
You will need to change that in the `update_name`-function.


## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
