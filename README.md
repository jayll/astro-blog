<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github.com/user-attachments/assets/18bd5c7e-3f45-4485-b4e8-6f0a45ca931d">
  <source media="(prefers-color-scheme: light)" srcset="https://github.com/user-attachments/assets/98d51208-2332-43e9-9ffb-787597644862">
  <img alt="Screenshot of blog template, main page." src="https://github.com/user-attachments/assets/98d51208-2332-43e9-9ffb-787597644862">
</picture>

[LIVE DEMO](https://flo-bit.dev/blog-template/)

# astro blog template

minimalistic but opinionated blog template using [astro](https://astro.build/) and [svelte](https://svelte.dev/). aims to be super easy to deploy and use, with a focus on performance and SEO, ease-of-use and design.

See a [live demo here](https://flo-bit.dev/blog-template/) (also doubles as a tutorial on how to use this template).

Features:

- ✅ 100/100 Lighthouse performance
- ✅ SEO-friendly with canonical URLs and OpenGraph data (automatically generated)
- ✅ Sitemap support
- ✅ RSS Feed support
- ✅ Markdown support
- ✅ Pagination
- ✅ Syntax highlighting (+ copy button)
- ✅ Dark and light mode with toggle button or auto-detect
- ✅ Search included
- ✅ Tags for posts
- ✅ Super easy to deploy as a static site
- ✅ Includes some prebuilt components for you to use
- ✅ Easy to edit by editing the markdown directly

## tutorials

the demo blog doubles as a tutorial on how to use this template:

- [quick start with cloudflare workers](https://flo-bit.dev/blog-template/posts/how-to-use)

- [adding content](https://flo-bit.dev/blog-template/posts/adding-content)

## quick start with cloudflare workers in 5 minutes

This blog is deployed to [cloudflare workers](https://developers.cloudflare.com/workers/static-assets/)
as a plain static site. `wrangler.jsonc` is committed on purpose: it tells cloudflare the site is an
assets-only worker, and it stops cloudflare's build system from trying to auto-configure an astro
adapter that a fully static site does not need.

1. Fork [the repository of this blog](https://github.com/flo-bit/blog-template)

2. In the cloudflare dashboard go to _Workers & Pages_ -> _Create_ -> _Import a repository_ and pick your fork

- **build command**: `npm run build`
- **deploy command**: `npx wrangler deploy`

Everything else (worker name, assets directory) is read from `wrangler.jsonc`.

3. Set up your blog info in `src/config.ts`, most importantly the `SITE` and `BASE` variables:

- `SITE`: the url your blog is served from, e.g. `https://astro-blog.<your-subdomain>.workers.dev`
(cloudflare shows it after the first deploy) or your own domain
- `BASE`: leave empty when the blog lives at the root of `SITE`, which is the normal case on cloudflare.
only set it (e.g. `/blog`) if you serve the blog from a subpath

4. Once you push your changes to main your blog should be live in about 1-2 minutes

5. Set up more info in `src/config.ts` (see [all options here](https://flo-bit.dev/blog-template/posts/configuring-the-blog))

- `SITE_TITLE` is the title of your blog, and will be shown in the header and in search results
- `SITE_DESCRIPTION` is the description of your blog, and will be shown e.g. in search results
- `SITE_FAVICON` is the emoji that will be shown as favicon of your blog (will be shown in the header and as favicon)
- `NAME` is the name of the author of the blog, will be shown in the footer as `(c) <YEAR> <NAME> - LICENSE`
- `SOCIAL_LINKS` set your social media links here, e.g. `{ GITHUB_URL: "https://github.com/<your-username>" }` 
will be shown in the footer of the blog

6. Edit `about.mdx` in `src/content/info/` to add your own about page.

7. Remove all files from `src/content/blog/` and add your own blog posts there. Time to write your first blog post! 
(see [adding content](https://flo-bit.dev/blog-template/posts/adding-content) for more info)

8. Anytime you push to the main branch, your blog will automatically be rebuilt and deployed. You can watch
the progress in the cloudflare dashboard under your worker's _Deployments_ tab.

You can also deploy straight from your own machine at any time:

```bash
npx wrangler login
npm run deploy
```

If you run into any issues with the template itself, feel free to
[open an issue](https://github.com/flo-bit/blog-template/issues)

## Notes

Search currently only works in production mode (i.e. when running `npm run build`) not in dev mode (`npm run dev`).

## Credits

Adopted from the default astro blog template when running `npm create astro@latest`.

## License

MIT.
