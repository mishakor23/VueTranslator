<template>
  <div id="app" class="text-center">
    <h1>Word Translator</h1>
    <h5></h5>
    <TranslateForm v-on:fromSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data () {
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText (text, language) {
      this.$http.get(`https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170720T134945Z.b3eefe5750b23ed8.12ccd0753f1a7d0650575a6c27a27b25caeee42b&lang=${language}&text=${text}`)
        .then(response => {
          this.translatedText = response.body.text[0]
        })
    }
  }
}
</script>

<style>
  body {
    background: #fefefe;
  }
  h1 {
    margin-bottom: 40px;
  }
</style>
