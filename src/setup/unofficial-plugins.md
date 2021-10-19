# Using 3rd-party Plugins

There is a growing ecosystem of unofficial community-made plugins for Bevy,
which provide a lot of functionality that is not officially included with
the engine. For many kinds/genres of games, you might greatly benefit from
using some of these.

To find such plugins, you should search the [Bevy
Assets](https://bevyengine.org/assets/) page on the official Bevy website. This
is the official registry of known community-made things for Bevy. If you
publish your own plugins for Bevy, you should [contribute a link to be added
to that page](https://github.com/bevyengine/bevy-assets).

Please beware that some 3rd-party plugins may use unusual licenses. Be sure
to check the license before using a plugin in your project.

---

Other pages in this book with valuable information when using 3rd-party plugins:

  - Some plugins may require you to [configure Bevy in some specific way](./bevy-config.md).
  - If you are [using bleeding-edge unreleased Bevy (main)](./bevy-git.md), you may encounter difficulties with plugin compatibility.

## Plugin Recommendations

This here is my personal, curated, opinionated list of recommendations,
featuring the most important plugins (in my opinion) in the Bevy ecosystem.

My goal here is to help direct new Bevy users to some known-good resources, so you can
start working on the kinds of games you want to make. :)

The plugins listed here are compatible with the latest Bevy release and use
permissive licenses (like Bevy itself).

This page is very limited. I can only recommend plugins I know enough
about. Please also check the [Bevy Assets](https://bevyengine.org/assets)
page to find even more things. :)

### Development Tools and Editors

[These are listed on a separate page.](./bevy-tools.md)

### Audio

Use [`bevy_kira_audio`](https://github.com/NiklasEi/bevy_kira_audio) instead of the built-in `bevy_audio`.

The built-in audio is very limited in features, and you are likely going to
need this plugin for pretty much any game with audio.

See [this page](../features/audio.md) for help on how to set it up.

### Tilemap

If you are making a 2D game based on a tile-map, there are plugins to
help do it efficiently with high performance. It is better to use one
of these plugins, instead of just spawning lots of individual Bevy
[Sprites](../features/sprites.md) for each tile.

  - [`bevy_ecs_tilemap`](https://github.com/StarArawn/bevy_ecs_tilemap)
    - Uses one ECS Entity per tile, with efficient custom rendering.
    - Lets you work with the tilemap in an ECS-idiomatic way.
    - Can be a little complex to set up / configure / spawn the tilemap.
    - Lots of features: Square/Hexagon/Isometric grids, animation, layers, chunks, optional ldtk/tiled support, ...
  - [`bevy_tilemap`](https://github.com/joshuajbouw/bevy_tilemap)
    - Another feature-rich plugin, but this one is not ECS-idiomatic (the whole map is one entity).
    - Designed to work well for infinite/endless or dynamically-generated maps.
    - API is quite refined and stable, has good documentation.
  - [`bevy_simple_tilemap`](https://github.com/forbjok/bevy_simple_tilemap)
    - Limited in features, easy to use if you just need to efficiently render a grid of square tiles.

### Shapes / Vector Graphics / Canvas

If you want to draw 2D shapes, use the
[`bevy_prototype_lyon`](https://github.com/Nilirad/bevy_prototype_lyon) plugin.

### Game AI

[`big-brain`](https://github.com/zkat/big-brain) is a fantastic plugin for game AI behaviors (Utility AI).

### GUI

If you want an alternative to Bevy UI, see [`bevy_egui`](https://github.com/mvlabat/bevy_egui).
This integrates the [`egui` toolkit](https://github.com/emilk/egui) into Bevy.

It is an immediate-mode GUI library (like the popular Dear Imgui, but in Rust).

It is very feature-rich and contains lots of widgets.

It was not really designed for making flashy gamey UIs (though it may very
well be fine for your game). It's great for editor-like UIs, debug UIs,
or non-game applications.

### Physics

Bevy can integrate with the [Rapier physics engine](https://rapier.rs/).

There are two plugins you can choose from:

  - [`bevy_rapier`](https://github.com/dimforge/bevy_rapier)
    - Maintained officially by the Rapier project developers.
    - This is a "raw" plugin that gives you direct access to Rapier.
    - Gives you the most control, but is hard to use and not idiomatic-Bevy.
    - You will probably need to read a lot of documentation, hard to learn.
  - [`heron`](https://github.com/jcornaz/heron)
    - An attempt to make a plugin that is more idiomatic to Bevy. More opinionated.
    - Likely to be easier to use and more intuitive than `bevy_rapier`.
    - May have more limited functionality.

### Animation

For simple "smooth motion" (easing/tweening/interpolation), try
[`bevy_easings`](https://crates.io/crates/bevy_easings). This might be good
enough for moving 2D objects around, moving the camera, or other such transitions.

For animating 2D sprites, try [`benimator`](https://github.com/jcornaz/benimator).

For 3D skeletal animation, unfortunately, there do not seem to be plugins yet.

Also, a long time ago, there was [this PR](https://github.com/bevyengine/bevy/pull/1429)
with an attempt to contribute a full-featured animation system to Bevy. To
my knowledge, it has not (yet) been made available as a separate plugin.

### Code Helpers

[`bevy_loading`](https://github.com/inodentry/bevy_loading) is a helper for
[state](../programming/states.md) transitions. It lets you register systems
that report their progress, tracks the progress, and transitions to the next
state when they are all ready. Most useful for loading screens, but can be used
more generally. Can also track the loading of [assets](../features/assets.md).

[`bevy_asset_loader`](https://github.com/NiklasEi/bevy_asset_loader) is a
more flexible and opinionated helper for managing and loading game assets.
Uses custom annotations to let you declare your assets more conveniently.