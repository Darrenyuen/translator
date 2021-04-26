<template>
  <div id="translateForm">
    <form v-on:submit="formSubmit">
        <input type="text" v-model="textToTranslate" placeholder="请输入需要翻译的内容"/> //v-model 双向绑定，对应的数据在data中声明
        <select v-model="lang">
            <!-- <option value="3">English</option> -->
            <option value="1">中文</option>
        </select>
        <input type="submit" value="翻译"/>
    </form>
  </div>
</template>

<script>
export default {
  name: 'TranslateForm',
  data: function() {
      return {
          textToTranslate: "",
          lang: ""
      }
  },
  methods: {
      formSubmit: function(e) {
        /**
         * 1中文 2日文 3英文 4韩文 5法文 6俄文 7葡萄牙文 8西班牙文 9auto 此处可以使用9或者auto
         * api示例： http://route.showapi.com/32-9?showapi_appid=612414&showapi_sign=a8e0c50ea4b94c1aa2560272b06e9041&q=hello&fromLanguage=3&toLanguage=1
         * 响应示例：{
                  "showapi_res_error": "",
                  "showapi_res_id": "60868ae58d57ba4170e47091",
                  "showapi_res_code": 0,
                  "showapi_res_body": {"ret_code":0,"translation":["你好"],"showapi_fee_num":1,"basic":{"ukPh":"həˈləʊ","wfs":[{"wf":{"name":"复数","value":"hellos"}},{"wf":{"name":"第三人称单数","value":"helloes"}},{"wf":{"name":"现在分词","value":"helloing"}},{"wf":{"name":"过去式","value":"helloed"}},{"wf":{"name":"过去分词","value":"helloed"}}],"usPh":"həˈləʊ","explains":["int. 喂；哈罗，你好，您好（表示问候， 惊奇或唤起注意时的用语）","vi. 说（或大声说）“喂”；打招呼","n. “喂”的招呼声；打招呼，问候","n. （Hello）（法）埃洛（人名）"],"ph":"həˈləʊ","exam_type":["初中","高中","CET4","CET6","考研"]},"requestId":"a79457a5-cd35-48a9-b275-dbc600af3643","isWord":true,"showapi_fee_code":0,"returnPhrase":["hello"]}
                }
                
         */
        //   alert(this.textToTranslate)
        // let result
                // console.log(this.lang)
        //使用vue-resource进行网络通信
        //js promise
        this.$http.get('http://route.showapi.com/32-9?showapi_appid=612414&showapi_sign=a8e0c50ea4b94c1aa2560272b06e9041&q=' + this.textToTranslate + '&fromLanguage=9&toLanguage=' + this.lang)
            .then((response)=> {
                // result = response
                // console.log(this.response)
                // console.log(response.body.showapi_res_body.basic.explains[0])
                this.$emit("translatedText", response.body.showapi_res_body.basic.explains[0]) //与父组件进行通信
            })
        // this.$emit("translatedText", result)
        e.preventDefault()
      }
  }
}
</script>

<style>

</style>
