# photography

A street photography site built with [Hugo](https://gohugo.io/) using the
[hugo-theme-gallery](https://github.com/nicokaiser/hugo-theme-gallery) theme.

## Adding photos

Create a folder per album under `content/`, containing an `index.md` front
matter file plus the JPEG images for that album, e.g.:

```
content/street/
├── index.md
├── photo-1.jpg
└── photo-2.jpg
```

Mark a specific image as the album cover in the front matter:

```yaml
resources:
  - src: photo-1.jpg
    params:
      cover: true
```

Since these are scans from film, EXIF metadata (capture date, description) is
not used for titles or sorting — `hugo.toml` disables EXIF date/description
extraction. Set titles and dates explicitly in front matter instead:

```yaml
resources:
  - src: photo-1.jpg
    title: A photo title
    params:
      date: 2026-01-01
```


## Local development

```sh
hugo server -D
```

Then open http://localhost:1313/.

## Deployment

Pushing to `main` triggers [.github/workflows/hugo.yml](.github/workflows/hugo.yml),
which builds the site with Hugo and publishes it via GitHub Pages.

In the repository settings, under **Settings → Pages**, set **Source** to
**GitHub Actions** (one-time setup).

