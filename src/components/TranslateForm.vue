<template>
<div id="translate-form" class="container">
 <form @submit.stop='formSubmit' role="form" class="row">
      <input type="text"  v-model="inputText"  placeholder="请输入要翻译的内容" class="form-control col-lg-6"/>
      <select v-model="defaultTranlateIndex" class="form-control col-lg-6">
        <option 
          v-for='(item,index) of translateList' 
          :key="index"
           :value="item.value">{{item.text}}</option>
      </select>
      <input type="submit" value="提交" class="btn btn-primary">      
    </form>
</div>
    
</template>
<script>
export default {
  name: "TranslateForm",
  data() {
    return {
      inputText: "",
      translateList: [
        {
          value: "en",
          text: "English"
        },
        {
          value: "ko",
          text: "Korean"
        },
        {
          value: "ru",
          text: "Russian"
        }
      ],
      defaultTranlateIndex: "en"
    };
  },
  methods: {
    formSubmit() {
      let self = this;
      this.$http
        .get(
          "https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181029T090347Z.f10d529bb9b867e0.802ade551d8acf71e854d2af44bd0153a58bf181&text=" +
            this.inputText +
            "&lang=" +
            this.defaultTranlateIndex
        )
        .then(res => {
          this.$emit("formSubmit", res.body.text[0]);
        });
    }
  }
};
</script>
<style lang='scss'>
#translate-form {
  display: flex;
  justify-content: center;
}
</style>

