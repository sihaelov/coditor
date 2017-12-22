<template>
  <div id="content">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'app',
};
</script>

<style>

html, body{
  background-color: #eee;
  height: 98%;
}

#content{
  margin: 20px;
}

#content,
#content > .row{
  height: calc(100% - 10px);
}

</style>
