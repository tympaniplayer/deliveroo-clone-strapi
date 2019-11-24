<template>
  <client-only>
    <nav class="uk-navbar-container" uk-navbar>
      <div class="uk-navbar-left">
        <ul class="uk-navbar-nav">
          <li class="uk-activate">
            <nuxt-link class="navbar-brand" to="/" exact>
              Deliveroo clone
            </nuxt-link>
          </li>
          <li>
            <nuxt-link class="navbar-brand" to="/restaurants" exact>
              Restaurants
            </nuxt-link>
          </li>
        </ul>
      </div>
    </nav>
  </client-only>
</template>
