<template>
  <div class="row">

    <div class="col s6 fields-wrapper">
      <htmlcode @codeChange="htmlCodeChange" v-bind:code="htmlCodeValue"></htmlcode>
      <csscode @codeChange="cssCodeChange" v-bind:code="cssCodeValue"></csscode>
    </div>

    <div class="col s6 output">
      <iframe
        ref="iframe"
        id="output-iframe"
        sandbox="allow-forms allow-scripts allow-same-origin allow-modals allow-popups" />
    </div>

  </div> <!-- /. row -->
</template>

<script>


import csscode from './CSSCode';
import htmlcode from './HTMLCode';

export default {
  components: {
    csscode,
    htmlcode,
  },
  name: 'Homepage',
  data() {
    return {
      htmlCodeValue: '<div></div>',
      cssCodeValue: 'div{\n  height: 100px; \n  width: 100px; \n  background: blue;\n}',
    };
  },
  methods: {
    htmlCodeChange(htmlNewCode) {
      this.htmlCodeValue = htmlNewCode;
      this.updateIframe();
    },
    cssCodeChange(cssNewCode) {
      this.cssCodeValue = cssNewCode;
      this.updateIframe();
    },
    updateIframe() {
      const iframe = this.$refs.iframe;
      const iframedoc = iframe.contentDocument || iframe.contentWindow.document;
      iframedoc.body.innerHTML = this.htmlCodeValue;

      let header = '<meta http-equiv="content-type" content="text/html; charset=UTF-8">';
      header += `<style type="text/css">${this.cssCodeValue}</style>`;

      iframedoc.head.innerHTML = header;
    },
  },
  mounted() {
    this.updateIframe();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

textarea{
  border: 0;
}

.output{
  background-color: #fff;
  height: 100%;
}
.output > iframe{
  height: 100%;
  width: 100%;
  border: 0;
}

.fields-wrapper{
  height: 100%;
}

.field .CodeMirror{
  /* height: 250px; */
  height: auto;
}

.field{
  background-color: #fff;
  margin-bottom: 20px;
  height: calc(50% - 10px);
}

.field > h2{
  font-size: 15px;
  padding: 13px 20px 5px;
  border-bottom: 1px solid #eee;
  color: #aaa;

  margin-bottom: 10px;
  margin-top: 0;
}

.field .CodeMirror-gutters{
  background-color: #fff;
  border: none;
}

.field .CodeMirror-linenumber{
  min-width: 10px;

  font-size: 13px;
  line-height: 22px;
}


</style>
