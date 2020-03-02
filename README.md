# Gatsby Starter Ghost

A starter template to build lightning fast websites with [Ghost](https://ghost.org) & [Gatsby](https://gatsbyjs.org)

**Demo:** https://gatsby.ghost.org

&nbsp;

![gatsby-starter-ghost](https://user-images.githubusercontent.com/120485/50913567-8ab8e380-142c-11e9-9e78-de02ded12fc6.jpg)

&nbsp;


# Installing

```bash
# With Gatsby CLI
gatsby new gatsby-starter-ghost https://github.com/TryGhost/gatsby-starter-ghost.git
```

```bash
# From Source
git clone https://github.com/TryGhost/gatsby-starter-ghost.git
cd gatsby-starter-ghost
```

Then install dependencies

```bash
yarn
```

&nbsp;

# Running

Start the development server. You now have a Gatsby site pulling content from headless Ghost.

```bash
gatsby develop
```

By default, the starter will populate content from a default Ghost install located at https://gatsby.ghost.io.

To use your own install, you will need to edit the `.ghost.json` config file with your credentials. Change the `apiUrl` value to the URL of your Ghost site. For Ghost(Pro) customers, this is the Ghost URL ending in `.ghost.io`, and for people using the self-hosted version of Ghost, it's the same URL used to access your site.

Next, update the `contentApiKey` value to a key associated with the Ghost site. A key can be provided by creating an integration within Ghost Admin. Navigate to Integrations and click "Add new integration". Name the integration appropriately and click create.

To use this starter without issues, your Ghost installation needs to be at least on version `2.10.0`.

The default Ghost version that is used for this starter is `3.x`. If your Ghost installation is on a lower version, you will need to pass in a `version` property in your `.ghost.json` settings:

**Ghost >=2.10.0 <3.0.0**
```json
{
    "apiUrl": "https://gatsby.ghost.io",
    "contentApiKey": "9cc5c67c358edfdd81455149d0",
    "version": "v2"
}
```

**Ghost <=3.0.0**
```json
{
    "apiUrl": "https://gatsby.ghost.io",
    "contentApiKey": "9cc5c67c358edfdd81455149d0"
}
```

&nbsp;

# Deploying with Netlify

The starter contains three config files specifically for deploying with Netlify. A `netlify.toml` file for build settings, a `/static/_headers` file with default security headers set for all routes, and `/static/_redirects` to set Netlify custom domain redirects.

To deploy to your Netlify account, hit the button below.

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/TryGhost/gatsby-starter-ghost)

Content API Keys are generally not considered to be sensitive information, they exist so that they can be changed in the event of abuse; so most people commit it directly to their `.ghost.json` config file. If you prefer to keep this information out of your repository you can remove this config and set [Netlify ENV variables](https://www.netlify.com/docs/continuous-deployment/#build-environment-variables) for production builds instead.

Once deployed, you can set up a [Ghost + Netlify Integration](https://docs.ghost.org/integrations/netlify/) to use deploy hooks from Ghost to trigger Netlify rebuilds. That way, any time data changes in Ghost, your site will rebuild on Netlify.

&nbsp;

# Optimising

You can disable the default Ghost Handlebars Theme front-end by enabling the `Make this site private` flag within your Ghost settings. This enables password protection in front of the Ghost install and sets `<meta name="robots" content="noindex" />` so your Gatsby front-end becomes the source of truth for SEO.

&nbsp;

# Extra options

```bash
# Run a production build, locally
gatsby build

# Serve a production build, locally
gatsby serve
```

Gatsby `develop` uses the `development` config in `.ghost.json` - while Gatsby `build` uses the `production` config.

&nbsp;

# Copyright & License

Copyright (c) 2013-2020 Ghost Foundation - Released under the [MIT license](LICENSE).

## Development

Se creó una cuenta en Heroku y usando la configuración del siguiente repositorio se instaló Ghost en una instancia de Heroku.

https://github.com/gndx/ghost-on-heroku

Al momento de crear la instancia solamente se agregaron los valores a nombre de la aplicación y url, también pidió que tuviera una tarjeta de crédito asociada a la cuenta para hacer el despliegue.

Se instaló Gatsby de manera global en el computador.

```shell
npm install -g gatsby-cli
```

Después se creó el proyecto de Gatsby usando el starter de Ghost

´´´shell
gatsby new codeblog https://github.com/TryGhost/gatsby-starter-ghost
´´´

Se borró el directorio .git para iniciar uno nuevo con mis propios commits y se crea el repositorio en GitHub para sincronizarlo.

En la parte de configuraciones de nuestro sitio en Ghost creamos una nueva custom integration y copiamos el API URL y el Content API Key en el archivo .ghost.json

La url también la cambiamos en el archivo `src/utils/siteConfig.js`

Se creó una cuenta en Netlify y se crea un nuevo sitio, ahí elegimos el repositorio de GitHub y realizamos el deploy

Una vez desplegado vamos a la configuración y en Build & deploy construimos un nuevo hook para integrar la api de Heroku, le damos un nombre y listo.
