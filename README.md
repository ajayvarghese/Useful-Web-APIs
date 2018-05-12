# Useful-Web-APIs
JavaScript APIs in the Web Platform which can be used improving User experience.

### Detect Browser Tabchange in webapp

```sh
window.addEventListener('visibilitychange', () => {
  switch(document.visibilityState) {
    case 'prerender':
      console.log('Tab is pre-rendering');
      break;
    case 'hidden':
      console.log('Tab is hidden');
      break;
    case 'visible':
      console.log('Tab is focused');
      break;
  }
});
```

### Detect Network Status
Listener for network change
```sh
console.log(navigator.onLine ? 'online' : 'offline')
window.addEventListener('offline', networkStatus)
window.addEventListener('online', networkStatus)
```

### Detect Device Orientation
Can be used for moving UI elements depending on device's orientation. alpha, beta, gama values can be taken for calculating transform values for the UI element.
eg: Facebook 360 video which moves as we move the device around.
```sh
window.addEventListener('deviceorientation', e => {
    console.log('GAMMA', e.gamma);
    console.log('BETA', e.beta);
    console.log('ALPHA', e.alpha);
});
```
### Battery Status
For getting Battery information
```sh
navigator.getBattery().then( battery => {
    console.log('BATTERY LEVEL', battery.level * 100, '%');
    battery.addEventListener('levelchange', () => {
        console.log(this.level * 100, '%');
    })
})
```

### Clipboard
```sh
let btn = document.getElementById('btn');
const selectContent = () => {
    let input = document.getElementById('someInput');
    input.focus();
    input.setSelectionRange(0, input.value.length);
}

const copyContent = () => {
    try {
        document.execCommand('copy');
    } catch(e) {
        console.log('error copying', e);
    }
}
btn.addEventListener('click', e => {
    selectContent();
    copyContent();
});
```
Also it comes with listeners for copy, cut and paste
```sh
document.addEventListener('cut', e => console.log(e.target.value))
document.addEventListener('copy', e => console.log(e.target.value))
document.addEventListener('paste', e => console.log(e.clipboardData.getData('text/plain')))
```

Usecase: Copy an entire block of code by just using a button.

### Vibration
Set vibration for mobile devices for cases like form validations and when showing errors.
###### Vibrate for 1s
```sh
navigator.vibrate(1000)
```
###### Vibrate with a pattern
```sh
navigator.vibrate([400, 300, 300, 200, 500])
// vibrate, wait, vibrate, wait, vibrate
```
###### Turn Vibrate off
```sh
navigator.vibrate(0)
```

### Ambient Light
Exposes sensor data which uses light intensity. Can be used to identify whether its dark or cloud.
```sh
window.addEventListener('devicelight', e => {
    console.log(e.value, ' lux');
})
```

