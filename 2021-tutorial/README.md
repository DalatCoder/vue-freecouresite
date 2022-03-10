# VueJS Course for Beginners [2021 Tutorial]

[See more](https://www.youtube.com/watch?v=FXpIoQ_rT_c&t=394s)

## 1. VueJS directives

- `v-cloak`: pause the app until it already loaded
- `v-model`: 2 ways binding, bind the input to the variable
- `v-if`: conditional insert element to the `DOM`
- `v-show`: conditional set the `display` attribute to `none`

Basic app

```vue
    <script>
      let options = {
        data: function () {
          return {
            greeting: 'Hello Vue 3!',
            isVisible: true,
          };
        },
      };
      let app = Vue.createApp(options);

      app.mount('#app');
    </script>
```
