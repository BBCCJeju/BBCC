<template lang="html">
  <div>
    <v-card >
      <div class="card-image">
          <!-- <img :src="bookData.img"> -->
          <img src="http://materializecss.com/images/sample-1.jpg">

          <span class="card-title">{{bookData.title}}</span>
      </div>
      <div class="v-card-content">
          <p>
              I am a very simple v-card. I am good at containing small bits of information.
          </p>
      </div>
      <div class="v-card-action">
          <a href="#">This is a link</a>
      </div>
    </v-card>
  </div>
</template>

<script>
export default {
  props: ['bookData'],
  methods: {
    
  }
}
</script>
