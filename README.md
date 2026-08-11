# Anti-Tamper | Issues

> [!WARNING]
> 🚧 The application is in an active stage of development
> //

## How it should work?

JS/TS module -> Parser -> Analyzer's -> IR -> Optimizer -> Verifier -> Transpiler -> VM

### Examples now

<table><tbody><tr><td width="500px"> Raw </td><td width="500px"> Transformed </td></tr><tr>
<td valign="top">

```js
/** @virtualize */
function compute(n) {
  let acc = 1;
  for (let i = 0; i < n; i = i + 1) {
    acc = (acc * 1664525 + 1013904223) % 4294967296;
    acc = acc + i * 3 - (acc % 17);
  }
  return acc;
}
```

</td><td valign="top">

```js
import { boot as _b } from "./049179b6.js";
export const antiTamperBench = {
  target: "compute",
  args: [2_000_000],
  warmup: 3,
  runs: 5,
};
const _rt = await _b();
const _m0 = await _rt.register(
  "f:131:321",
  new URL("./aa43f4cb.atbc", import.meta.url),
  0,
);
function compute(__at_arg_0) {
  return _m0.invokeSync(1362294170, this, new.target, undefined, arguments);
}
export { compute };
```

</td></tr></tbody></table>
