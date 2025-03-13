# Layouts

- **`layouts/default.vue`:** The default layout that applies to all pages unless you specify a different layout.

- **Custom Layouts:** Create additional files in the `layouts/` directory (e.g., `layouts/blog.vue`).

- **Using Layouts in Pages:** Specify the layout to use within your page component:

  ```vue
  <script>
  export default {
    layout: "blog", // Use the 'blog.vue' layout
  };
  </script>
  ```

- **`<Nuxt>` Component:** Within your layout files, use the `<Nuxt />` component to render the content of the current page.

  ```vue
  <template>
    <div>
      <header></header>
      <main>
        <Nuxt /> {/* This is where the page content will be rendered */}
      </main>
      <footer></footer>
    </div>
  </template>
  ```
