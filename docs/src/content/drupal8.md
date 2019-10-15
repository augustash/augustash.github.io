---
title: "Drupal 8 Local Development Setup"
date: "2019-10-14"
draft: false
path: "/docs/drupal8"
---
There are 2 primary setups for Drupal 8 sites, composer based and non-composer based. We are moving forward with a composer based setup.

**Prerequisites**
* Locally configured web server (Apache or Nginx)
* Node
* NPM
* Drush

## Initial Site Setup.
- Pull the site down locally from Pantheon or GitHub.
- Pull a copy of the database locally
- Pull a copy of the files
- Setup your local DNS
- Generate a `settings.local.php` file within `web/sites/default`
  - Update database connection info.
- Clear your cache via `drush cr`

## Theme Setup.
- Pull the site down locally from Pantheon or GitHub
- Move into the site directory you just pulled down `cd SITENAME`
- For a composer based Drupal install you should see a `web` directory in the root of your project.
  - NOTE: If it is a Pantheon project, we commit the vendor directory and installed modules by default.
- For Theme updates, move into the theme directory from the root `cd web/themes/ash/`
  - **Note**: If there is a `dev` folder, move into the dev folder as well `cd dev` or `cd web/themes/ash/dev`
  - If there is **NO** `dev` directory stay in the root of the theme `web/themes/ash/`
  - Run `npm install` from within that directory.
- Run the following comand to compile SASS and watch for changes within the theme - `gulp`
  - If you run into an error such as "Node Sass does not yet support your current environment"
    - Try and run `npm rebuild node-sass`
- To utilize **BrowserSync**, copy `example.config.local.json` as `config.local.json` and update the `proxy` line with your local development URL

