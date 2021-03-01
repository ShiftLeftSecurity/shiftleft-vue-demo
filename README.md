# sl-vue

Sample app to test Vue.js 2 with ShiftLeft NG SAST.

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

## Testing the vulnerabilities

Navigate to the About page and try pasting the following in the override text fields

```
<img src="notValidUrl" onerror=alert(document.cookie)>
```

```
<a onmouseover=alert(document.cookie)>click me!</a>
```

Try clicking the `Load Remote Data` button which renders a vulnerable REST api response without sanitization.


### Compiles and minifies for production
```
yarn build
```

### Run your unit tests
```
yarn test:unit
```

### Lints and fixes files
```
yarn lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
