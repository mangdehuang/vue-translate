<template>
<div id="translateText">
  <div>翻译后内容</div>
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
<style>
</style>

