<template>
  <div class="field">
      <h2>HTML</h2>
      <codemirror
        ref="myCm"
        :value="code"
        :options="cmOptions"
        @input="onCmCodeChange">
      </codemirror>
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
  props: ['code'],
  data() {
    return {
      cmOptions: {
        // tabSize: 4,
        line: true,
        lineNumbers: true,
        mode: 'htmlmixed',
      },
    };
  },
  methods: {
    onCmCodeChange(newCode) {
      this.$emit('codeChange', newCode);
    },
  },
  computed: {
    codemirror() {
      return this.$refs.myCm.codemirror;
    },
  },
};
</script>

<style scoped>

</style>
