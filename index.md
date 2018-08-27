title: Web Components
class: animation-fade
layout: true

.bottom-bar[
  {{title}}
]

---

class: impact

# {{title}}

Steven Bassett, UI Engineering
---

## Outline

* Introduction to Web Components
* Introduction to Stencil
* Why we chose to use Stencil?
* How we are planning to use Web Components?


???
Today I am going to talk about web components, a tool to build them, why we chose that tool and how we are planning on using them here.

---

## Web Components

* Natively-supported, standardized JavaScript components
* Run in every framework or on their own
<!-- * Answer to the shared-component problem -->
* Powered by the [Custom Element spec](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements)
* [Native browser support][browser-support]: Chrome, Safari, Firefox (in v63) and great polyfills

[browser-support]: https://caniuse.com/#feat=custom-elementsv1
???

Web Components are built into the open web platform. They have come a long ways since their first intorduction in 2015.

Since they are just built on the open web, they are easy to be used in any frontend frameworks or on their own

They help us encapsulate shared components across a large site.

At their core, they are powered by the Custom Elements API that allow us to define our own tags.

Browser support is progressing much faster. Custom Elements have landed in Chrome, Safari, and soon FireFox. There are great polyfills for browsers that do not support them yet.

---

## Custom Element Example

```js
class MyTabs extends HTMLElement {
    createdCallback() { /* Standard DOM/fetch/etc. code... */}
    attachedCallback() {}
    detachedCallback() {}
    attributeChangedCallback() {}
}

customElements.define('my-tabs', MyTabs);
```
???
Custom elements are defined by creating a class that extend the HTMLElement. The class can take advantages of lifecycle hooks like knowing when the element has been created or when an HTML attribute changes.

---
## Custom Element Example (cont.)

```html
<my-tabs>
  <my-tab active tab-title="general" slot="tabs">
    ...
  </my-tab>
</my-tabs>
```

???
Using a custom element is as simple as writing HTML or using the standard DOM apis.

Attributes and properties are the primary way we communicate to these elements.

CustomEvents allow us to dispatch callbacks and cummunicate to the rest of the page.

---
## How can we make building custom elements easier?

* Still want framework features
* Desire to manage bundles of components
* Great developer experience

???
While the platform APIs give us powerful ways of writing custom elements, much of what a frontend developer expects is missing.

Managing the bundling and build optimization required a lot of setup.

Writing vanilla components lack some great developer tools like typescript, hot realoading and dev tools.

---

## .max-height-100[![Stencil](stencil-logo.svg)]

* A compiler that generates Custom Elements, part of the Web Components spec
* Not a framework: output is 100% standards-compliant Custom Elements
* Adds powerful framework features to Web Components, with only 6kb overhead


<small>[Stencil Documentation](https://stenciljs.com/)</small>

???
Stencil is a web component compiler instead of a framework. It provides a compiler that includes most of the features we expect in a full framwork. Yet it's output is just custom elements that can be used everywhere.

It has a very small overhead and it is easy to get started.
---

## Example Stencil Component

```jsx
import { Component, Prop } from '@stencil/core';

@Component({ tag: 'my-name', styleUrl: './my-name.scss' })
export class MyName {
  @Prop() name: string;
  render() {
    return <p>Hello, my name is {this.name}</p>;
  }
}
```
???



---
## Compiled Components Have:

- **Virtual DOM**: fast DOM updates without common DOM performance pitfalls
- **Lazy Loading**: By default components load asynchronously.
- **Reactivity**: Efficient updates based on property and state changes
- **High-performance Rendering**: async rendering system, similar to React Fiber
- **JSX**: Popular and familiar markup system pioneered by React
- **Server Side Rendering**: Hydrate pre-compiled components on the server without a headless browser

---
## Why we chose Stencil?

* **Performance**: Traditional frameworks proving too heavy while we migrate from angular.
* **Interoperability**: Ability to create components that work across all major frameworks.
* **Familiarity**: features from frameworks but in a leaner, standards-compliant package
* **Developer Productivity**: Features like hot reloading and CSS encapsulation make our team faster.

---
## Performance

**Cached**
<iframe src="./lighthouse-cached.html" width="100%" height="60%"></iframe>

---
## Performance
**First Visit**
<iframe src="./lighthouse.html" width="100%" height="60%"></iframe>

---

## How we are using web components today?

* Already in use on production with our cookie, mobile alert banners.
* Migration of the component library.
* The creation of standalone site wide navigation application.
* Bolt native application aware components, with communication built in.

---

## How to get started in your existing applications?

```bash
yarn create stencil
```


---
### Tips:
* Start simple, start by building new components in your current app.
* Use redux to share application state from angular & stencil.
* Stencil router for component routing.
* Use pre-rendering for a blazing fast start up time.


---
class: impact

## Questions?

Reach out on ask-ui-engineering
