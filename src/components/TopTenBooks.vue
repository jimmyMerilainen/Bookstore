<template>
  <div>
    <div>
      <b-list-group>
        <h4 class="text-left">Top 10</h4>

        <b-list-group-item
          v-for="(product, index) in topTen.slice(0, 10)"
          :key="index"
          class="d-flex justify-content-between"
          :to="{ name: 'Product', params: { isbn: product.isbn } }"
        >
          <div class="text-left">
            <h6>
              <span class="top-ten">{{ index + 1 }}.</span> {{ product.title }}
            </h6>

            <small>{{ product.author }}</small>

            <p>Price: ${{ product.price }}</p>
            <b-rating
              inline
              :value="product.rating"
              size="sm"
              readonly
              no-border
            ></b-rating>
          </div>

          <div>
            <div>
              <img :src="product.image" width="70" height="100" />
            </div>
          </div>
        </b-list-group-item>
      </b-list-group>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },

  created() {
    console.log(this.books);
  },

  computed: {
    topTen() {
      this.topTenRating();
      return this.$store.state.topTenBooks;
    },
  },
  methods: {
    topTenRating() {
      this.$store.state.topTenBooks.sort(function(a, b) {
        return b.rating - a.rating;
      });
    },
  },
};
</script>

<style scoped>
h6 {
  margin-bottom: 0rem;
}
p {
  color: red;
  margin-top: 0rem;
  margin-bottom: 0rem;
}
small {
  margin-top: 0rem;
}
.top-ten {
  color: red;
}
b-rating {
  padding: 0rem 0rem;
  margin: 0rem;
  text-align: right;
}
</style>
