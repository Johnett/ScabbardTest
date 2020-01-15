# Frequently Asked Questions

Have a question that isn't part of the FAQ? Please search [Github Issues](https://github.com/arunkumar9t2/scabbard/issues).

## Does it support mixed Kotlin/Java projects?

Yes.

## What is the impact on binary size?

There should be no impact since Scabbard only runs during compilation and generated images are not meant to be packaged into binary. You could control if Scabbard is enabled for release builds via `scabbard { enabled = false }` block.

## What is the impact on build time?

1. Scabbard processor uses standard annotation processing APIs to generate images. This lets the processor be cacheable and does not run when inputs have not changed.

2. Currently there are no benchmark available and more work is expected to be done in performance area.

## How can I understand the generated graph?

Please refer to Scabbard [cheat sheet](cheat-sheet.md).

## Will more formats (svg) be supported?

Yes, there are plans to support more formats. Please 👍 this [issue](https://github.com/arunkumar9t2/scabbard/issues/8).

## I don't see gutter icons to view graph.

Please wait for Android Studio/IntelliJ indexing to be done for gutter icons to be visible. Even after indexing if the icons are not visible, please file an issue. You could also look for generated `png` file in the `build` folder.

## Some dependencies are missing.

In order to keep graphs small and readable, Scabbard groups the dependencies by `@Component` or `@Subcomponent` and renders them in individual graphs.

This has the benefit of keeping the graphs readable for large projects but this structure might not properly render cross component dependencies (inherited bindings in a subcomponent). Some work is being doing in this area, please refer [#7](https://github.com/arunkumar9t2/scabbard/issues/7).

## Any other format for visualizing the dependency graph?

Some other graph formats being considered are:

* **Component Tree**: Render component and subcomponents in a tree structure similar to [Uber Ribs.](https://1fykyq3mdn5r21tpna3wkdyi-wpengine.netdna-ssl.com/wp-content/uploads/2018/11/Carbon_architecture_Figure_02.gif)
* **Single graph**: Instead of splitting the graph into multiple files, render all nodes in single file [#6](https://github.com/arunkumar9t2/scabbard/issues/6).