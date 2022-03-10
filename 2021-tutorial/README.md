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

## 2. Events & Methods

To handle events

- Use directive: `v-on:[event]`: `v-on:click="isVisible = !isVisible"`
- Use `@`: `@click="isVisible = !isVisible"`
- Use `@` with handler method: `@click="toggleBox"`
- Use `@` with handler method with parameters: `@click="toggleBox(1, 2, 3)"`

Event modifier

- `keyup` event: `@keyup="greet(greeting + '!!!!!')"`
- `keyup` event fired only when user press the `enter` key: `@keyup.enter="greet(greeting + '!!!!!')"`
- `@click.right`: fired when user click the right mouse
- `@click.prevent`: `preventDefault`

## 3. Components

Break out the app into some small components

```vue
    <login-form />
```

```vue
    app.component('login-form', {
    template: `
        <form @submit.prevent="handleSubmit">
        <h2>{{ title }}</h2>
        <input type="email" v-model="email" />
        <input type="password" v-model="password" />
        <button>Login</button>
        </form>
    `,
    data: function () {
        return {
        title: 'Login Form',
        email: '',
        password: '',
        };
    },
    methods: {
        handleSubmit() {
        alert(this.email + ' ' + this.password);
        },
    },
    });
```
