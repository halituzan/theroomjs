# theroomjs
> A vanilla javascript plugin that allows you to outline dom elements like web inspectors.

[![NPM](https://nodei.co/npm/theroomjs.png)](https://nodei.co/npm/theroomjs/)

`theroomjs` can be accessable globally as `theRoom`. It's compatible with modern browsers such as Google Chrome, Mozilla Firefox, Safari, Edge and Internet Explorer.

## Options

| Name              | Type               | Default    | Description                         |
| ---               | ---                | ---        | ---                                 |
| inspector         | string or DOM node | -          | Placeholder element for inspection. It will not be inspected  |
| htmlClass         | boolean            | true       | If `true` namespace theRoom will be automatically added to `<html>` element class list |
| blockRedirection  | boolean            | false      | If `true` the page will not be redirected elsewhere. The library will override `onbeforeunload` for prevention |
| excludes          | array              | -          | Element list that excluded for inspection. Basic CSS selectors are allowed. For more information please see [document.querySelector](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector) |

## Events

| Name       | Description                                              |
| ---        | ---                                                      |
| starting   | Fired when inspection is being started inspection        |
| started    | Fired when inspection is started inspection              |
| stopping   | Fired when inspection is being stopped                   |
| stopped    | Fired when inspection is stopped                         |
| click      | Fired when inspected element is clicked. The element will be passed as first argument  |
| mouseover  | Fired when inspected element mouseovered. The element will be passed as first argument |
| hook       | Fired at the very beginning of `click` and `mouseover` event listeners. [Event](https://developer.mozilla.org/en-US/docs/Web/API/Event) passed as argument |

> Events can also be defined in options.

## theRoom object

`theRoom` object contains properties which are listed in below table.

| Option            | Type     | Parameters                          | Description                                               |
| ---               | ---      | ---                                 | ---                                                       |
| on                | function | `event name` and `handler function` | Event binder (dynamic binding supported)                  |
| start             | function | `options`                           | Inspection starter function                               |
| stop              | function | -                                   | Inspection stopped function                               |
| status            | function | -                                   | Returns inspection engine status. Can be `idle`, `running` and `stopped` |

## Usage

```javascript
  // start inspection
  window.theRoom.start({
    inspector: '.inspector-element',
    blockRedirection: true,
    excludes: ['footer'],
    click: function (element) {
      console.log('the element is clicked:', element)
    }
  })

  // dynamically event binding
  window.theRoom.on('mouseover', function (element) {
    console.log('the element is hovered', element)
  })

  // stop inspection
  window.theRoom.stop()

  // log the current status
  console.log(
    window.theRoom.status() // will print out -> stopped
  )
```

## Contribution
Contributions and pull requests are kindly welcomed!

## License
This project is licensed under the terms of the [MIT license](https://github.com/hsynlms/theroomjs/blob/master/LICENSE).
