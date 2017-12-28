<template>
  <div class="field">
    <h2>CSS</h2>
    <codemirror
      ref="myCm"
      :value="code"
      :options="cmOptions"
      @input="onCmCodeChange">
    </codemirror>
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
  props: ['code'],
  data() {
    return {
      cmOptions: {
        lineNumbers: true,
        mode: 'css',
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
