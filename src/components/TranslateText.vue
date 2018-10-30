<template>
<div id="translate-text">
  <div>{{tranlatedText}}</div>
</div>
  
</template>
<script>
export default {
  name: "TranslateText",
  props: {
    tranlatedText: String
  }
};
</script>
<style lang='scss'scoped>
#translate-text {
  // display: flex;
  // justify-content: center;
}
</style>

