title: Web Components
class: animation-fade
layout: true

<!-- This slide will serve as the base layout for all your slides -->
.bottom-bar[
  {{title}}
]

---

class: impact

# {{title}}
## Frameworks agnostic, better performance and future friendly.

---
## Outline

* Introduction to Web Components
* Introduction to Stencil
* Why we chose to use Stencil?
* How we are planning to use Web Components?

---
## Web Components

* Natively-supported, standardized JavaScript components
* Run in every framework or on their own
* Answer to the shared-component problem
* Powered by the Custom Element spec
* Native browser support: Chrome, Safari, Firefox (in v63) and great polyfills

---
## Custom Element Example

```html
<my-tabs theme="light">
  <my-tab active tab-title="general">...</my-tab>
</my-tabs>
```

---
## Custom Element Example

```js
class MyTabs extends HTMLElement {
	createdCallback() {
		// Standard DOM/fetch/etc. code...
	}
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
* Many teams are choosing TypeScript

---

## Stencil JS

* A compiler that generates Custom Elements, part of the Web Components spec
* Not a framework: output is 100% standards-compliant Custom Elements
* Adds powerful framework features to Web Components

---
## Example Stencil Component
```typescript
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

## Stencil-Compiled Components Have

* Virtual DOM: fast DOM updates without common DOM performance pitfalls
* Lazy Loading: By default components load asyncronously and can be bundled with related components
* Reactivity: Efficient updates based on property and state changes
* Feature detection and polyfill loading to support all browsers.
* High-performance Rendering: async rendering system, similar to React Fiber
* JSX: Popular and familiar markup system pioneered by React
* Server Side Rendering: Hydrate pre-compiled components on the server without a headless browser

---

## Why we chose Stencil?

* Performance: Traditional frameworks proving too heavy for demanding mobile Progressive Web Applications
* Stability: Desire to use web standards and avoid constant framework churn
* Interoperability: Ability to create components that work across all major frameworks.
* Familiarity: features from frameworks but in a leaner, standards-compliant package

---

## How we are using web components today

* Global Components
* Migration of existing angular directives to standard web components
* How they integrate into a angular.js app?

---
