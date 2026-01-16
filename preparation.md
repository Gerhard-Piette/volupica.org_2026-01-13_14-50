# Preparation of dev envy










## Installation of plugins


Installed these plugins during installation:
- @nuxt/a11y
- @nuxt/content
- @nuxt/eslint
- @nuxt/scripts
- better-sqlite3

Additionally:
- npx nuxt@latest module add sitemap
- npm install --save-dev prettier eslint-config-prettier










## Added files

- .prettierrc
- content.config.ts
- Copied icon file and logo file to "public" folder.
- Copied "assets" folder into "app" folder.
- Copied "layouts" folder into "app" folder.
- Copied "pages" folder into "app" folder.
- Replaced app.vue file in "app" folder.
- Added app/router.options.ts. This makes the browser return to the position before the link jump when clicking the back button.










## Modified files

- esling.config.mjs
- nuxt.config.ts











## vscode settings

{
  "editor.formatOnSave": false, 
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  },
  "eslint.validate": ["javascript", "typescript", "vue"]
}



