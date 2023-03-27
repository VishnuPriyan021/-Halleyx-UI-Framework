<h1 align="center"
 style="display:flex:align-item:center;">
 <img src="./src/assets/img/logo.png" style="object-fit:fit;width:25px"> HalleyxUI
</h1>
<h4 align="center">

The real McCoy thing

[![NPM][npm-badge]][npm-url]
[![HalleyxUI][ci-badge]][ci-url]
[![Development Status][alpha-badge]][npm-url]
[![License][license-badge]][license-url]

[_Introduction_](#introduction) &mdash;
[_Components_](#components) &mdash;
[_Getting Started_](#quick-start) &mdash;
[_License_](#license)

</h4>

## Introduction
&emsp;Halleyx UI kit a collection of UI elements and assets, curated to serve for every designer's and developer's need.

### Components
&emsp;The following components are currently on the orbit.
- [Accordion]()
- [Notification]()
- [Badge]()
- [Breadcrumb]()
- [Button]()
- [Calendar]()
- [Card]()
- [Color pallete]()
- [Dashboard]()
- [Dataview]()
- [Divider]()
- [Dotted pagination]()
- [Draggable]()
- [Drawer]()
- [Error page]()
- [File uploader]()
- [Image gallery]()
- [Import progress bar]()
- [Input]()
- [Input elements]()
- [Label]()
- [Loader]()
- [Modal]()
- [Pagination]()
- [Rating]()
- [Search]()
- [Select]()
- [Sidebar]()
- [Signup page]()
- [Slider]()
- [Speed dial]()
- [Stepper]()
- [Tab]()
- [Table]()
- [Tag]()
- [Text editor]()
- [Time line]()
- [Tree view]()
- [Tree select]()

## Installation
<p style="display:flex;align-item:center;">
<b>NPM</b> <img src="https://badge.fury.io/js/halley-kit.svg" style="margin-left:10px;">
</p>

```
npm install halleyx-ui
```
## Quick start
&emsp;This section describes how to use <strong>Halley kit</strong> in your project.

 **Global import**

&emsp;Config module with project globally
```
//main.js
import { createApp } from "vue";
import App from "./App.vue";
import halleyxComponents from "halleyx-ui";
//load the styles
import 'halley-kit/dist/umd/index.css';
createApp(App).use(halleyxComponents).mount("#app");
```
**Local import**

  &emsp;Config module with project locally

  ```
//main.js
import { createApp } from "vue";
import App from "./App.vue";
import halleyxComponents from "halleyx-ui";
//load the styles
import 'halley-kit/dist/umd/index.css';
createApp(App).use(halleyxComponents).mount("#app");
```
```
<!-- Any vue component-->
<template>
  <hlx-button class="primary">Button</hlx-button>
</template>

<script>
import {HlxButton} from 'halley-kit';
export default {
  name: 'App',
  components: {
    HlxButton,
  },
}
<\/script>
```



## License
&emsp;Tenzir UI-Component Library comes with a [3-clause BSD license][license-url].

<!-- Github -->
[ci-url]: https://github.com/halleyx-com/UI-kit.git
[ci-badge]: https://badgen.net/badge/icon/HalleyKit?icon=github&label
<!-- NPM -->
[npm-badge]: https://badgen.net/badge/icon/halley-kit?icon=npm&label
[npm-url]: https://www.npmjs.com/package/halley-kit
<!-- License -->
[license-badge]: https://img.shields.io/badge/license-BSD-blue.svg
[license-url]: https://github.com/tenzir/ui-components/blob/master/COPYING
[alpha-badge]: https://img.shields.io/badge/stage-alpha-blueviolet
<!-- Future -->
[contributing-url]: 
[latest-release-badge]: 
<!-- [latest-release-url]:  -->