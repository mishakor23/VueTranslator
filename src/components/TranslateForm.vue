<template>
  <div id="translateForm" class="row">
    <div class="col-md-6 col-md-offset-3">
      <form v-on:submit="formSubmit" class="well trans-from form-inline">
        <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a word">
        <select class="form-control" v-model="language">
          <option value="uk">Ukrainian</option>
          <option value="fr">French</option>
          <option value="en">English</option>
          <option value="es">Spanish</option>
          <option value="zh">Chinese</option>
        </select>
        <input class="btn btn-primary" type="submit" value="Translate">
      </form>
  </div>
  </div>
</template>

<script>
export default {
  name: 'TranslateForm',
  data () {
    return {
      textToTranslate: '',
      language: ''
    }
  },
  created () {
    this.language = 'zh'
  },
  methods: {
    formSubmit (e) {
      this.$emit('fromSubmit', this.textToTranslate, this.language)
      e.preventDefault()
    }
  }
}
</script>

<style>
  .trans-from {
    border: 1px #ccc solid;
    border-radius: 10px;
  }
</style>
