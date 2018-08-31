 <template lang="html">
     <div class="list__items">
       <ul class="list-group">
          <VideoListItem
             :video="video"
             v-for="video in videos"
             :key="video.etag"
             @videoSelect="onVideoSelect">
          </VideoListItem>
       </ul>
     </div>

</template>

<script>
    import VideoListItem from './VideoListItem.vue';
    export default {

        name: 'VideoList',
        props:['videos'],
        methods:{
            onVideoSelect(video){
                // console.log(video)
                this.$emit('videoSelect', video)
            }
        },
        components:{
            VideoListItem
        }
    }
</script>

<style lang="css">
</style>
