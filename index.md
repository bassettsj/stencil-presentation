title: Web Components
class: animation-fade
layout: true

.bottom-bar[
  {{title}}
]

---

class: impact

# {{title}}
## Frameworks agnostic, better performance and future friendly.

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
* Answer to the shared-component problem
* Powered by the [Custom Element spec](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements)
* [Native browser support][browser-support]: Chrome, Safari, Firefox (in v63) and great polyfills

[browser-support]: https://caniuse.com/#feat=custom-elementsv1
???

Web Components are built into the open web platform. They have come a long ways since their first intorduction in 2015.

Since they are just built on the open web, they are easy to be used in any frontend frameworks or on their own

They help us encapsulate shared components across a large site.

At their core, they are

---

## Custom Element Example

```html
<my-tabs>
  <my-tab active tab-title="general" slot="tabs">...</my-tab>
</my-tabs>
```

```js
class MyTabs extends HTMLElement {
    createdCallback() { /* Standard DOM/fetch/etc. code... */}
    attachedCallback() {}
    detachedCallback() {}
    attributeChangedCallback() {}
}

document.registerElement('my-tabs', MyTabs);
```

---
## How can we make building custom elements easier?

* Still want framework features
* Desire to manage bundles of components
* Provide code splitting out of the box
* Great developer experience

---

## .max-height-100[![Stencil](stencil-logo.svg)]

* A compiler that generates Custom Elements, part of the Web Components spec
* Not a framework: output is 100% standards-compliant Custom Elements
* Adds powerful framework features to Web Components, with only 6kb overhead


[Stencil Documentation](https://stenciljs.com/)
---

## Example Stencil Component

```jsx
import { Component, Prop } from '@stencil/core';

@Component({ tag: 'my-name', styleUrl: 'my-name.scss' })
export class MyName {
  @Prop() name: string;
  render() {
    return <p>Hello, my name is {this.name}</p>;
  }
}
```

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
