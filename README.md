# Slade Construction & Building website
This folder contains the static website for Slade Construction & Building, a construction company serving Dublin and Wicklow. The website source and assets are in [`public/`](public/).

## Pages
- `index.html` — homepage and services overview
- `about.html` — company information
- `projects.html` — project portfolio
- `project-single.html` — project detail layout
- `careers.html` — careers information and application form
- `index2.html` — alternate homepage draft

## Preview locally
There is no build step or package manager configuration. Serve the `public` directory with any static web server, then open its `index.html`. For example, from this folder:
```sh
python3 -m http.server 8000 --directory public
```
Visit <http://localhost:8000/> in a browser. Serving the files over HTTP keeps relative asset paths working consistently.

## Project structure
```text
public/
    ├── *.html          Website pages
    ├── style.css       Site styles
    ├── css/vendor.css  Vendor styles
    ├── images/         Logos and project imagery
    ├── fonts/          Icon font files
    └── js/             Site scripts and bundled libraries
.gitignore
LICENSE
railway.toml
README.md
```
The pages use Bootstrap 5, Bootstrap Icons, Swiper, and Work Sans. Bootstrap, Bootstrap Icons, Swiper, and Google Fonts are loaded from CDNs; an internet connection is needed for those resources. The local `js/` folder contains the site's scripts and supporting libraries.

## Docker
Build and run the site from this folder (`/`):

```sh
docker build -t slade-construction-website .
docker run --rm -p 8080:8080 slade-construction-website
```

Open <http://localhost:8080/>. The Nginx container serves the contents of `public/` and uses Railway's `PORT` variable when deployed.

For Railway, set the service Root Directory to `/dark`. The included [`railway.toml`](railway.toml) selects the Dockerfile in that directory.

## Updating the site
Edit the HTML files in `public/` and shared styles in `public/style.css`. Keep links and asset paths relative to `public/` so the pages continue to work when hosted as a static site. Check the pages at desktop and mobile widths after making layout changes.
Before publishing, connect the enquiry and careers forms to the intended form service or backend and confirm their destinations. The current HTML includes form actions that may refer to pages or services not included in this folder.

## Template attribution
The site is based on the TemplatesJungle Rentiz Bootstrap template. The original template usage terms and credits are in [`public/readme.txt`](public/readme.txt); retain the required attribution unless the appropriate license permits its removal.