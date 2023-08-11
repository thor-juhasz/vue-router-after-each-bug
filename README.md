# test-vue-router

This project was created with `yarn create vue`, with TS ESlint and vue-router. Everything else was default.

```shell
$ yarn set version latest
$ yarn install
```

### Code changes for reproduction

This added in the `AboutView.vue` component:

```vue
<script setup lang="ts">
import { onBeforeRouteLeave } from 'vue-router';

onBeforeRouteLeave(() => {
    return false;
});
</script>
```

and this addter in the `router/index.ts` file:

```typescript
router.afterEach(() => {
   console.log('afterEach !');
});
```

### Run the project

```shell
$ yarn dev
```
Then open the page, and go to the "About" page.
Now click the "Home" page, or use the browser back button.

You will see that the Vue router does indeed block the navigation, but the `afterEach` listener is still executed.
