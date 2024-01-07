
# Integrating motion-canvas with quarto

This is a demo of how to integrate [quarto](https://quarto.org) with
[motion canvas](https://motioncanvas.io).

Quarto is a project that allows you to embed R, Python and other
languages in a markdown document, and render this into various outputs,
including HTML documents and websites.

Motion-canvas is a project to create code-first animations. You write
the animations in TypeScript, and can render (export) the animation as
video files, or embed as JavaScript in websites.

Since browsers typically don’t understand TypeScript, you first have to
convert the animations to JavaScript. This conversion is done using a
build chain of `node` programs, in particular `vite`. To command
`npm run build` triggers a `node` build, as defined by `package.json`.

This build will create a set of bundled outputs (JavaScript files) in
the `dist` folder. Your quarto doc can then refer to these bundled
outputs and thus embed the animations.

## Live preview

This project contains a quarto website, defined in `quarto.qmd`.

You can preview the rendered version of this site at
<https://andrie.quarto.pub/motion-canvas/>

## Folder structure

The folder structure of this project is as follows:

``` bash
.
├── README.md
├── _quarto.yml
├── index.qmd
├── motion-canvas-ts.html # Inject the mc dependencies
├── package.json
├── vite.config.ts
├── src
│   ├── main.ts # 
├── animations
│   ├── # motion canvas files go here
|   ├── vite.config.ts
|   ├── src
|   |   ├── project.ts
|   |   ├── scenes
|   |   |   ├── example.ts
├── dist
|   ├── # compiled motion canvas files go here
```

## Building the project

### Build the animations

The animations are in the `animations` folder, structured in the typical
`motion-canvas` way, with a `animations/rc/project.ts` and
`animations/src/scenes/scene.tsx files.`

To build the animations, run:

    npm --prefix animations run build

This will create the bundled JavaScript files in `/public/animations`

### Build the main project

To build the main project, run:

``` bash
npm run build
```

This will create the `/dist` folder, containing the main JavaScript
files that embeds all of `motion-canvas`, as well as the animation files
in `/dist/animations`

### Build the quarto doc

Build the quarto project:

``` bash
quarto preview
quarto render
```

## Acknowledgement

This integration was inspired by the work of @hhenrichsen and the
example of integrating `motion-canvas` into a `vite` website and hosted
on github, via Github Actions builders.

https://github.com/hhenrichsen/motion-canvas-github-actions
