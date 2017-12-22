<template>
  <div class="field">
      <h2>HTML</h2>
      <codemirror v-model="code" :options="cmOptions"></codemirror>
  </div>
</template>

<script>
// import CodeMirror from 'codemirror'
import { codemirror } from 'vue-codemirror';

import 'codemirror/mode/htmlmixed/htmlmixed';
import 'codemirror/lib/codemirror.css';

export default {
  name: 'htmlcode',
  components: {
    codemirror,
  },
  data() {
    return {
      code: '',
      cmOptions: {
        // codemirror options
        // tabSize: 4,
        line: true,
        lineNumbers: true,
        mode: 'htmlmixed',
      },
    };
  },
  methods: {
    onCmReady(cm) {
      console.log('the editor is readied!', cm);
    },
    onCmFocus(cm) {
      console.log('the editor is focus!', cm);
    },
    onCmCodeChange(newCode) {
      console.log('this is new code', newCode);
      this.code = newCode;
    },
  },
  computed: {
    codemirror() {
      return this.$refs.myCm.codemirror;
    },
  },
  // mounted() {
  //   console.log('this is current codemirror object', this.codemirror);
  //   // you can use this.codemirror to do something...
  // },
};
</script>

<style scoped>

</style>
