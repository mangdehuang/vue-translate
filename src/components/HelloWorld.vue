<template>
  <div id="hello">
    <div class="title">在线翻译</div>
    <translate-form @formSubmit='formSubmit'></translate-form>
    <translate-text :tranlatedText='tranlatedText'></translate-text>
  </div>
</template>

<script>
import TranslateForm from "./TranslateForm";
import TranslateText from "./TranslateText";
export default {
  name: "HelloWorld",
  data() {
    return {
      tranlatedText: ""
    };
  },
  components: {
    TranslateForm,
    TranslateText
  },
  methods: {
    formSubmit(text) {
      this.tranlatedText = text;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='scss' scoped>
#hello {
  .title {
    display: flex;
    justify-content: center;
  }
}
</style>
