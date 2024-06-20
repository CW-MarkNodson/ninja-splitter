# ninja-splitter

<p align="left">
  <a href="https://www.npmjs.com/package/ninja-splitter">
    <img src="https://img.shields.io/npm/v/ninja-splitter?color=orange&label=Ninja-splitter%20npm&logo=Ninja-splitter" alt="Ninja-splitter on npm" />
  </a>
  <a href="https://www.npmjs.com/package/ninja-splitter">
    <img src="https://img.shields.io/npm/dt/ninja-splitter" alt="Total downloads of Ninja-splitter" />
  </a>
</p>

Splitter component for Angular 16+


Inspired by https://github.com/wannabegeek/ng2-split-pane. (Can be used up to Angular 8)

There are 2 types of split panes: `horizontal-ninja` and `vertical-ninja`

## Install
-------
You can either [download](https://github.com/iSerganov/ninja-splitter/archive/master.zip)
the whole project or install it via NPM:

```bash
$ npm install ninja-splitter
```
-------

The following configuration properties are available to client code:

Key | Range | Does
--- | --- | ---
`primary-minsize` | value in pixels | Minimal allowed size for primary pane
`secondary-minsize` | value in pixels | Minimal allowed size for secondary pane
`separator-width-px` | value in pixels (5 by default) | The thickness of the separator between the primary and secondary components
`primary-component-toggle` | boolean `true` or `false` (false by default) | Hide the primary component and the separator
`secondary-component-toggle` | boolean `true` or `false` (false by default) | Hide the secondary component and the separator
`primary-component-initialratio` | initial value in a ratio of primary/secondary (range 0-1) | The initial size to create the primary pane (secondary will fill the remaining), this value will be over-ridden if a value is found in the local storage.
`local-storage-key` | string value used as the local storage key key  | If this value is present the current splitter position will be stored in local storage


## Styling
-------
You can define the following css variables to override default styling:

CSS-variable | Responsible for | Default
--- | --- | ---
`--ninja-separator-background-color` | Background color of the separator HTML element | #fff
`--ninja-separator-hover-background-color` | Hover background color of the separator HTML element | #fafafa
`--ninja-separator-hcursor` | Horizontal separator cursor | ns-resize
`--ninja-separator-vcursor` | Vertical separator cursor | ew-resize

## Example
-------
```javascript
<horizontal-ninja
    primary-minsize="50"
    secondary-minsize="100"
    [primary-component-toggle]="false"
    [secondary-component-toggle]="condition"
    local-storage-key="ninja"
    primary-component-initialratio="0.8">

    <div class="ninja-content-primary">
        <span>
            Upper pane
        </span>
    </div>

    <div class="ninja-content-secondary">
        <span>
            Lower pane
        </span>
    </div>

</horizontal-ninja>

```
**Import**
```typescript
// Please note the module is not in the root
import { NinjaSplitterModule } from 'ninja-splitter';

@NgModule({
    declarations: [
        AppComponent
    ],
    imports: [
        NinjaSplitterModule
    ],
    bootstrap: [AppComponent]
})
export class AppModule { }
```

## Events

`(on-change)` - emitted on resizing

`(on-begin-resizing)` - emitted when the user begins dragging the separator

`(on-ended-resizing)` - emitted when the user releases the separator after dragging
