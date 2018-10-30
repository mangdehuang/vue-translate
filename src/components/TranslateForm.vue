<template>
<div id="translate-form">
 <form @submit.stop='formSubmit' role="form" class="form-horizontal">
      <div class="form-group">
          <label for="name" class="col-lg-offset-2  col-md-offset-2 col-lg-3 col-md-3 col-sm-2 control-label">翻译内容</label>
          <div class="col-lg-3 col-sm-5">
            <input type="text"  v-model="inputText"  id='name' placeholder="请输入要翻译的内容" class="form-control"/>
          </div>
      </div>
      <div class="form-group" >
          <label for="translateType"  class="col-lg-offset-2  col-md-offset-2 col-lg-3 col-md-3 col-sm-2 control-label">语言选择</label>
          <div class="col-lg-3 col-sm-5">
             <select v-model="defaultTranlateIndex" id='translateType' class="form-control col-lg-6">
                <option 
                  v-for='(item,index) of translateList' 
                  :key="index"
                  :value="item.value">{{item.text}}</option>
            </select>
          </div>
      </div>
      <div class="form-group">
        <input type="submit" value="提交" class="btn btn-primary  col-lg-offset-5 col-md-offset-6 col-sm-offset-6">      
      </div>
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
}
</style>

