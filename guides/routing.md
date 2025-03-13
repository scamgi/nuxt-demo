# Working with Pages and Routing

- **Basic Routing:** As mentioned earlier, the `pages/` directory is the heart of routing.

- **Dynamic Routes:** Use square brackets `[]` in your filenames to create dynamic route parameters.

  - `pages/users/[id].vue`: This will match routes like `/users/1`, `/users/2`, `/users/abc`, etc. The value inside the brackets (`id` in this case) becomes a route parameter that you can access within your component.
  - Accessing route parameters: Inside your component, you can access the parameter using `$route.params.id` (or whatever you named your parameter).

- **Nested Routes:** Create nested directories within `pages/` to create nested routes.

  - `pages/products/index.vue` -\> `/products`
  - `pages/products/new.vue` -\> `/products/new`
  - `pages/products/[id].vue` -\> `/products/123`
  - `pages/products/[id]/edit.vue` -\> `/products/123/edit`

- **`<NuxtLink>` Component:** Use the `<NuxtLink>` component (instead of regular `<a>` tags) for internal navigation within your Nuxt application. This enables client-side navigation (without a full page reload), making your application feel faster and more responsive.

  ```vue
  <NuxtLink to="/about">About Us</NuxtLink>
  <NuxtLink
    :to="{ name: 'products-id', params: { id: 123 } }"
  >Product 123</NuxtLink>
  ```
