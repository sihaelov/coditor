<template>
  <div class="field">
      <h2>CSS</h2>
      <codemirror v-model="code" :options="cmOptions"></codemirror>
  </div>
</template>

<script>

import { codemirror } from 'vue-codemirror';

// import CodeMirror from 'codemirror';
import 'codemirror/mode/css/css';
import 'codemirror/lib/codemirror.css';

export default {
  name: 'csscode',
  components: {
    codemirror,
  },
  data() {
    return {
      code: '',
      cmOptions: {
        lineNumbers: true,
        mode: 'css',
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
