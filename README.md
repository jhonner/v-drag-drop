# v-drag-drop

**Minimalistic drag & drop directives for [Vue.js 2](https://vuejs.org/)**

Designed to encapsulate some of the peculiarities of the Drag & Drop API and make it easier to use with Vue.js.

## Table of Contents

* [Installation](#installation)
* [Usage](#usage)
* [API](#api)


## Installation

Install `v-drag-drop` via npm:

```bash
npm install --save v-drag-drop
```

Then import it in your project:

```javascript
import Vue from 'vue';
import vDragDrop from 'v-drag-drop';
Vue.use(vDragDrop);
```

Or include the files via `<script>` tag:
```html
<script src="node_modules/vue/dist/vue.min.js"></script>
<script src="node_modules/v-drag-drop/dist/vDragDrop.min.js"></script>
<script>
    Vue.use(vDragDrop);
</script>
```


## Usage

The following template example is the minimum setup required to get a draggable element and a drop zone with `v-drag-drop`:

```html
<div v-draggable="myData"></div>
<div v-droppable @drag-drop="handleDrop"></div>
```

This template example shows all the features supported by `v-drag-drop`. Check the [API section](#api) for details.

```html
<div v-draggable.move="myData"
     @drag-start="onDragStart"
     @drag-move="onDragMove"
     @drag-end="onDragEnd">
</div>

<div v-droppable
     @drag-enter="onDragEnter"
     @drag-over="onDragOver"
     @drag-leave="onDragLeave"
     @drag-drop="onDragDrop">
</div>
```

Also check the demos in the `demo` directory. You can run the demos with `npm run dev`.


## API

`v-drag-drop` provides two directives: `v-draggable` for draggable elements and `v-droppable` for drop zones.

### `v-draggable`

#### Value

This is the data you want to transfer to the drop zone. The data can be arbitrary objects or primitives.

Example:

```javascript
Vue.component('my-component', {
    template: '<div v-draggable="myData"></div>',
    data() {
        return {
            myData: { foobar: 42 }
        };
    }
});
```

#### Modifiers

* `move`: Optional. Add this modifier to get a crosshair cursor on the element: `v-draggable.move`

#### Events

All event listeners are called with the dragged data as first argument.

* `drag-start`: Fired when the user starts dragging.

* `drag-move`: Fired repeatedly while dragging is in progress.

* `drag-end`: Fired when dragging is finished.


### `v-droppable`

#### Value

Unused.

#### Events

All event listeners are called with the dragged data as first argument.

* `drag-enter`: Fired when a dragged item enters the drop zone.

* `drag-over`: Fired repeatedly while a dragged item is over the drop zone.

* `drag-leave`: Fired when a dragged item leaves the drop zone.

* `drag-drop`: Fired when an item has been dropped on the drop zone. Called with the dragged data only.