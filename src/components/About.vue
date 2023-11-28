<template>
  <div class="about">
    <h1>Hello {{their_name}}, this is an about page</h1>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore
      magna aliqua. Rhoncus mattis rhoncus urna neque viverra justo nec ultrices dui. Ultricies integer quis auctor elit
      sed vulputate mi sit amet. Urna cursus eget nunc scelerisque. Odio morbi quis commodo odio aenean sed adipiscing.
      Condimentum id venenatis a condimentum vitae sapien pellentesque habitant. Suspendisse potenti nullam ac tortor
      vitae purus faucibus ornare. Volutpat maecenas volutpat blandit aliquam etiam erat velit. Velit scelerisque in
      dictum non consectetur a erat nam at...</p>
  </div>
</template>

<script>
export default {
  name: 'About',
  data() {
    return {
      their_name: this.$route.params.name
    }
  },
}
</script>