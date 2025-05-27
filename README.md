# flo-bit portfolio

this is my portfolio, created using astro, svelte, threlte, threejs and tailwind. wip.

## demos

[see it live here](https://danishx.me/)

demo videos:

https://github.com/user-attachments/assets/d11be1e0-94c3-4a1a-a3d7-4943ee81a2a9

## techstack

- sveltekit (static build using `@sveltejs/adapter-static`)
- threlte (svelte wrapper for threejs)
- tailwind
- automatic deployment using github actions to github pages
- typescript

## development

clone the repo, install dependencies and run the dev server:

```bash
git clone https://github.com/danishistired/danishx.me-re.git
npm install
npm run dev
```

when using it for your own portfolio, please remove the posthog analytics script from `src/app.html` (line 3-6)
