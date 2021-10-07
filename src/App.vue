<template>
<div>
  <b-container>
    <b-row>
      <b-col>
    <GiphyViewer />
      </b-col>
    </b-row>  
  </b-container>
</div>  
</template>

<script>
import GiphyViewer from '@/components/GiphyViewer.vue'

export default {
  name: 'App',
  components: {
    GiphyViewer
  }
}
</script>

<style>


</style>
