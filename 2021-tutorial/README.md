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

## 4. Passing `props`

```vue
    app.component('login-form', {
    template: `
        <form @submit.prevent="handleSubmit">
        <h2>{{ title }}</h2>
        <custom-input :label="emailLabel" v-model="email" />
        <custom-input :label="passwordLabel" v-model="password" />
        <button>Login</button>
        </form>
    `,
    component: ['custom-input'],
    data: function () {
        return {
        title: 'Login Form',
        email: '',
        password: '',
        emailLabel: 'Email',
        passwordLabel: 'Password',
        };
    },
    methods: {
        handleSubmit() {
        alert(this.email + ' ' + this.password);
        },
    },
    });
```

```vue
    app.component('custom-input', {
    template: `
        <label>
        {{ label }}
        </label>
        <input type="text" v-model="inputValue" />
    `,
    props: ['label', 'modelValue'],
    computed: {
        inputValue: {
        get() {
            return this.modelValue;
        },
        set(value) {
            this.$emit('update:modelValue', value);
        },
        },
    },
```

## 5. Loops

```vue
app.component('login-form', {
    template: `
        <form @submit.prevent="handleSubmit">
        <h2>{{ title }}</h2>
        <custom-input 
            v-for="(input, idx) in inputs" 
            :key="idx" 
            :label="input.label" 
            :type="input.type" 
            v-model="input.value" 
        />
        <button>Login</button>
        </form>
    `,
    component: ['custom-input'],
    data: function () {
        return {
            title: 'Login Form',
            inputs: [
                {
                    label: 'Email',
                    value: '',
                    type: 'email',
                },
                {
                    label: 'Password',
                    value: '',
                    type: 'password',
                },
            ],
            email: '',
            password: '',
            emailLabel: 'Email',
            passwordLabel: 'Password',
        };
    },
    methods: {
        handleSubmit() {
            alert(this.inputs[0].value + ' ' + this.inputs[1].value);
        },
    },
});
```

## 6. Lifecycle Hooks

- Check if user is authorized
- API calls
- Creating or removing events
- Getting or cleaning up data
