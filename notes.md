pnpm init svelte@next windicss-override-sveltekit

cd windicss-override-sveltekit/

pnpm i -D vite-plugin-windicss

Now I import the plugin int the svelte.config.cjs file:

```javascript
// svelte.config.js
import preprocess from 'svelte-preprocess';
import WindiCSS from 'vite-plugin-windicss/dist/index.mjs'

/** @type {import('@sveltejs/kit').Config} */
const config = {
    // Consult https://github.com/sveltejs/svelte-preprocess
    // for more information about preprocessors
    preprocess: preprocess(),

    kit: {
        // hydrate the <div id="svelte"> element in src/app.html
        target: '#svelte',
        vite: {
            plugins: [
                WindiCSS(),
            ]
        }       
    },  
};

export default config;
```

create the src/routes/__layout.svelte

```
<!-- src/routes/__layout.svelte -->
<script>
  import 'virtual:windi.css';
</script>
<slot />
```

enter 

```html
<h1 class="bg-red-200 bg-green-300">Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
```

in src/index.svelte

```svelte
<!-- src/routes/__layout.svelte -->
<script>
  import 'virtual:windi.css';
</script>
<slot />
```

playground: https://windicss.org/play.html?html=DwCwjABAxgNghgZwQXgEQCMDmBaATgUwBNsAmABjIi20wPwDtsBmC1APggHV8YoB7ALb4IAFz4QAygDceI-AGkAliOAB6cGwBQm4AAc2ANUUJlEYHAggCAMzQgRI3QgBcq1QGtlAOgQyYcr0J8KXZPER8-AKCpNTgOMQgCOEJREGFCPigAVyF6ETgRRT56NX1tIA&css=HQIw9gHgBA3gUFKABAhgBzQGwJ4MVNbAWgA4CJSoBLAO01oFMiAzTB6AWwpQFcAXMHkQgA5kQDuACyp8GUACYoATgGsAXKKIilKYgBYADAYXL1msGhQBjGcQCMBoVCVgeNeQ3lEImKAGdJFHkwcSIOeX9LKyZiACYAbjgAXzhQPhpYPFQMHCc0Cj0CeyhZCD4iPw4S9nK0HiUsJgA2IyhmMBpyvwYOKnBMeScXNw8vZh5MX3AlDyUoadmiOoa2IljWxVUNMBmGJSX6xtIjJ0kwADc9tVLyqRk5M8ulDTFlo5bjR6uFvaI%2BHRofksSgYnSc7SsPD8alcfHoNCYNA6cghULUSloYlizkxBxWzVaGJoYgs1lsREMiRSQA