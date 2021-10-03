# Create Support for a new Platform

<!-- TODO: Add guidelines for what platforms will not be supported -->

## Write the extractor

It is best to make your extractor as light as possible. For this reason I would
recommend a rss-feed if the platform has one.

If you have chosen a rss-feed take a look at the implementation of the 
platform `Peertube`, you can copy-and-paste most of its code.
If your platform has special tags you need, you will have to edit the 
rss-structure defined in `tf_utils/src/rss.rss`. If your tag has `:`, replace 
them with `/` in the `rss.rs`-file and in the `lib.rs`-file (see `media:` and
`itunes:` as examples).

If your platform does not have a rss-feed or using one is not practical, you 
will have to do most of the work manually, see the `Youtube`-platform as a 
example.

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
