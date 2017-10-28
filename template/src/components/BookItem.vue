<template lang="html">
  <div>
      <i class="checkBtn fa fa-check" aria-hidden="true"></i>
        {{ bookData }}
        <span class="removeBtn" type="button">
            <i class="fa fa-trash-o" aria-hidden="true"></i>
        </span>
  </div>
</template>

<script>
export default {
  props: ['bookData'],
  methods: {
    
  }
}
</script>
