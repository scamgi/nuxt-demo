# Data Fetching

Nuxt provides several ways to fetch data for your components:

- **`asyncData` (RECOMMENDED for SSR):** This is a special hook that runs _on the server_ (during SSR) _and_ on the client (during client-side navigation). It's used to fetch data _before_ the component is created. The data returned from `asyncData` is merged into the component's `data`. This is the preferred method for fetching data that is essential for the initial rendering of the page.

  ```vue
  <script>
  export default {
    async asyncData({ params, $axios }) {
      // Context object provided by Nuxt
      try {
        const { data } = await $axios.get(`/api/products/${params.id}`);
        return { product: data }; // This will be merged into the component's data
      } catch (error) {
        // Handle errors appropriately, e.g., redirect to a 404 page
        console.error(error);
        return { product: null };
      }
    },
  };
  </script>
  ```

- **`fetch` (RECOMMENDED for Client-Side Updates):** The `fetch` hook is similar to `asyncData`, but it can be called multiple times (e.g., when a component is updated, or on user interaction). It's great for fetching data that might change over time, or for fetching data that's not essential for the initial render. It also runs on both the server and the client. Nuxt adds a `$fetchState` object to your component, which you can use to track the loading/error state of the fetch operation.

  ```vue
  <template>
    <div>
      <div v-if="$fetchState.pending">Loading...</div>
      <div v-else-if="$fetchState.error">
        Error: {{ $fetchState.error.message }}
      </div>
      <div v-else>
        <h1>{{ product.name }}</h1>
        <p>{{ product.description }}</p>
      </div>
    </div>
  </template>

  <script>
  export default {
    data() {
      return {
        product: null,
      };
    },
    async fetch() {
      try {
        const { data } = await this.$axios.get(
          `/api/products/${this.$route.params.id}`,
        );
        this.product = data;
      } catch (error) {
        console.error(error); // Handle the error appropriately
        // You might want to set an error message in your component's data
      }
    },
  };
  </script>
  ```

- **`created` / `mounted` (Less Preferred):** You _can_ fetch data in the standard Vue.js lifecycle hooks (`created` or `mounted`), but this is generally _not recommended_ for SSR. Data fetched in these hooks will _only_ be fetched on the client, so you won't get the benefits of SSR for that data. Use `asyncData` or `fetch` whenever possible.
