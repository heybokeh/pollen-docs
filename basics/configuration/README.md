# Configuration

While Pollen provides a default bundle of useful low-level variables to build your project with (under `pollen-css/pollen.css`), it also comes with a build tool to generate your own custom variables stylesheet that you can use in your project instead.

Start by creating a `pollen.config.js` file in the root of your project that exports either a function or an object. See the full list of configuration options below.

{% code title="pollen.config.js" %}
```javascript
module.exports = {
  // Config options
}
```
{% endcode %}

Once you have a configuration file, run the included `pollen` CLI tool. Either install `pollen-css` globally, or run the tool in an NPM script or with `npx`.

{% tabs %}
{% tab title="Global install" %}
```
$ npm i -g pollen-css
$ pollen
```
{% endtab %}

{% tab title="Local install" %}
```
npm i pollen-css
npx pollen
```
{% endtab %}
{% endtabs %}

Since the output CSS is generated by Pollen, we recommend excluding this output from version control like git and running the `pollen` build tool along with the rest of your build pipeline, in a CI step or similar. You can do this with a `prebuild` script in `package.json`

{% code title="package.json" %}
```json
{
  "scripts": {
    "prebuild": "pollen"
  }
}
```
{% endcode %}

### Config options

| Option    | Default               | Description                                                                                 |
| --------- | --------------------- | ------------------------------------------------------------------------------------------- |
| `output`  | `./pollen.css`        | File path of the generated Pollen stylesheet to use in your project                         |
| `modules` | Pollen default values | Pollen module configuration, see [configuring-modules.md](configuring-modules.md "mention") |

```javascript
module.exports = {
  output: './styles/pollen.css',
  modules: {
    // Module config
  }
}
```

### CLI options

| Option           | Default                          | Description                              |
| ---------------- | -------------------------------- | ---------------------------------------- |
| `-c`, `--config` | `./pollen.config.js`             | Path to your Pollen config file          |
| `-o`, `--output` | Value of `output` in config file | File path to generated Pollen stylesheet |

```
pollen -c ./pollen-dev.config.js -o ./styles/pollen-dev.css
```

### Typescript support

Pollen exports its config as a `Config` type, which you can use to annotate your config file with JSDoc typings

```javascript
/** @type {import('pollen-css').Config} */
module.exports = {}
```
