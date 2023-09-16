<script >
import InputTag from "./components/icons/inputTag.vue"
export default {
  components:{
    InputTag
  },
  methods:{
    handleOnTagsChange(tags){
      console.log(tags)
    }
  }
}
</script>

<template>
  <InputTag  :onTagsChangue="handleOnTagsChange" />
</template>

<style scoped>

</style>
