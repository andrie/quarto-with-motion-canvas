# Integrating quarto with motion canvas

This is a demo of how to integrate [quarto](https://quarto.org) with [motion canvas](https://motioncanvas.io).

## Folder structure

The folder structure of this project is as follows:

```bash
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

Build the animations

```
npm --prefix animations run build
```

Build the main project

```bash
npm run build
```

Build the quarto project

```bash
quarto preview
quarto render
```



