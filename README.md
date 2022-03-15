# v-perfect-signature

Pressure-sensitive signature drawing for Vue 2 and 3 built on top of [perfect-freehand](https://github.com/steveruizok/perfect-freehand).

Demo: https://wobsoriano.github.io/v-perfect-signature

## Install

```bash
yarn add v-perfect-signature
```

## Usage

```html
<script setup>
  import { ref } from 'vue';
  import VPerfectSignature from 'v-perfect-signature';

  const signaturePad = ref();
  const strokeOptions = {
    size: 16,
    thinning: 0.75,
    smoothing: 0.5,
    streamline: 0.5,
  };

  function toDataURL() {
    const dataURL = signaturePad.value.toDataURL();
    console.log(dataURL);
  }
</script>

<template>
  <VPerfectSignature :stroke-options="strokeOptions" ref="signaturePad" />
</template>
```

## Props

| Name              | Type   | Default                                                              | Description              |
| ----------------- | ------ | -------------------------------------------------------------------- | ------------------------ |
| `width`           | String | `100%`                                                               | Set canvas width         |
| `height`          | String | `100%`                                                               | Set canvas height        |
| `backgroundColor` | String | `rgba(0,0,0,0)`                                                      | Canvas background color  |
| `penColor`        | String | `#000`                                                               | Canvas pen color         |
| `strokeOptions`   | Object | [Reference](https://github.com/steveruizok/perfect-freehand#options) | Perfect freehand options |

## Methods

| Name                        | Argument Type                                                                                                           | Description                                                  |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| `toDataURL(type)`           | [String](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement/toDataURL)                                  | Returns signature image as data URL                          |
| `fromDataURL(dataUri)`      | [String](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Data_URIs)                                    | Draws signature image from data URL                          |
| `toData`                    | -                                                                                                                       | Returns signature image as an array of array of input points |
| `fromData(data)`            | [Array](https://github.com/wobsoriano/v-perfect-signature/blob/master/packages/lib/src/components/__tests__/mock.ts#L1) | Draws signature image from array of array of input points    |
| `clear()`                   | -                                                                                                                       | Clears the canvas                                            |
| `isEmpty()`                 | -                                                                                                                       | Returns true if canvas is empty                              |
| `resizeCanvas(shouldClear)` | `Boolean`                                                                                                               | Resizes and recalculate dimensions                           |

Note: Like [signature_pad](https://github.com/szimek/signature_pad), `fromDataURL` does not populate internal data structure. Thus, after using `fromDataURL`, `toData` won't work properly.

## Events

| Name      | Type     | Default | Description             |
| --------- | -------- | ------- | ----------------------- |
| `onBegin` | Function | -       | Fired when stroke begin |
| `onEnd`   | Function | -       | Fired when stroke end   |

## Build and publish

```bash
cd packages/lib/
pnpm install
pnpm build
npm publish
```

## Credits

- [perfect-freehand](https://github.com/steveruizok/perfect-freehand) - Draw perfect pressure-sensitive freehand strokes.
- [signature_pad](https://github.com/szimek/signature_pad) - HTML 5 canvas based smooth signature drawing.
- [vue-signature-pad](https://github.com/neighborhood999/vue-signature-pad) - Vue wrapper of signature_pad.
- [vue-demi](https://github.com/vueuse/vue-demi/) - Creates Universal Library for Vue 2 & 3

## License

MIT - Copyright (c) 2022 [Robert Soriano](https://github.com/wobsoriano)
