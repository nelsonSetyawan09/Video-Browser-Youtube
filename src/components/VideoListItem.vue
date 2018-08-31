<template lang="html">
  <li class="list__item list-group-item" @click="onVideoSelect">
    <img :src="thumbnailsUrl" alt="video_thumbnails" class="list__thumbnails">
    <div class="list__title">
         <p>{{video.snippet.title}}</p>
    </div>
  </li>
</template>

<script>
    export default {
        name: 'VideoListItem',
        props:['video'],
        methods:{
            onVideoSelect(){
                this.$emit('videoSelect', this.video)
            }
        },
        computed:{
            thumbnailsUrl(){
                return this.video.snippet.thumbnails.default.url;
            }
        }
    }
</script>

<style lang="css" scoped>
    li{
        display: flex;
    }
    li:hover{
        cursor: pointer;
        background-color: #eee;
    }
    .list__thumbnails{
        margin-right: 10px;
    }
</style>
