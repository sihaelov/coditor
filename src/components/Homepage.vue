<template>
  <div class="row">

    <div class="col s6 fields-wrapper">
      <htmlcode></htmlcode>
      <csscode></csscode>
    </div>

    <div class="col s6 output">
      <iframe id="output-iframe"
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
  font-size: 10px;

  line-height: 15px;
}

</style>
