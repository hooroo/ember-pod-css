# ember-pod-css

Based on [Ember Component CSS](https://github.com/ebryn/ember-component-css)

## Installation

Add `"ember-pod-css": "git@github.com:hooroo/ember-pod-css.git"` to your bower.json and run `bower install`
Add `"ember-pod-css": "git+ssh://git@github.com:hooroo/ember-pod-css.git"` to packages.json and run `npm install`

## Usage

This addon allows you to specify a `styles.css` file inside of your component's pod folder (`app/my-component/styles.css`).

Rules defined inside of these `styles.css` files will automatically be namespaced with an autogenerated class. That autogenerated class will also be injected into your component's `classNames` property. This enables you to worry less about rules clashing across component styles. The classes generated will use the folder name for the template with a prefix of parent folders hyphenated.

For example, given this `app/my-component/styles.css` file:

```css
& {
  padding: 2px;
}
.urgent {
  color: red;
}
```

Your generated CSS output will look something like:

```css
.my-component {
  padding: 2px;
}
.my-component .urgent {
  color: red;
}
```

You can also do the same with normal templates in your pods.

Given this 'app/companies/employee/style.css' file:

```css
& {
  padding: 2px;
}
.urgent {
  color: red;
}
```

Your generated CSS output will look something like:

```css
.companies-employee {
  padding: 2px;
}
.companies-employee .urgent {
  color: red;
}
```

A typical component invocation that looks like this:

`{{my-component}}`

will generated markup like:

`<div class="my-component"></div>`

### With Preprocessors

To use this addon with another preprocessor (such as Sass or Less), simply import `pod-styles` into your base app stylesheet.

For example, if you're using Sass:

```scss
// app/styles/app.scss
@import "pod-styles";
```

And that is it! The `pod-styles` file is generated during the build and will then be pulled into your other stylesheet to be processed like normal.

**Approved preprocessors:**

 - [`ember-cli-sass`](https://github.com/aexmachina/ember-cli-sass)
 - [`ember-cli-less`](https://github.com/gdub22/ember-cli-less)
 - [`ember-cli-stylus`](https://github.com/drewcovi/ember-cli-stylus)
