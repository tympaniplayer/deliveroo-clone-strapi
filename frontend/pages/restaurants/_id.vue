<template>
  <div>
    <a @click="$router.go(-1)" class="uk-button uk-button-primary uk-margin">
      <span uk-icon="arrow-left" /> Go back
    </a>

    <client-only>
      <div uk-grid>
        <div class="uk-width-1-3@m">
          <div v-for="dish in restaurant.dishes" v-bind:key="dish.id" class="uk-margin">
            <div class="uk-card uk-card-default">
              <div class="uk-card-media-top">
                <img :src="'http://localhost:1337/' + dish.image.url" alt>
              </div>
              <div class="uk-card-body">
                <h3 class="uk-card-title">
                  {{ dish.name }}
                  <span class="uk-badge">${{ dish.price }}</span>
                </h3>
                <p>{{ dish.description }}</p>
              </div>
              <div class="uk-card-footer">
                <button @click="addToCart(dish)" class="uk-button uk-button-primary">
                  Add to cart
                </button>
              </div>
            </div>
          </div>
        </div>
        <div class="uk-width-expand@m">
          <Cart />
        </div>
      </div>
    </client-only>
  </div>
</template>

<script>
import { mapMutations } from 'vuex'
import Cart from '~/components/Cart.vue'
import restaurantQuery from '~/apollo/queries/restaurant/restaurant'

export default {
  components: {
    Cart
  },
  data () {
    return {
      restaurant: Object
    }
  },
  apollo: {
    restaurant: {
      prefetch: true,
      query: restaurantQuery,
      variables () {
        return { id: this.$route.params.id }
      }
    }
  },
  methods: {
    ...mapMutations({
      addToCart: 'cart/add',
      removeFromCart: 'cart/remove'
    })
  }
}
</script>
