<template lang="html">
    <div class="video" >
        <div class="details" v-if="video">
            <div class="embed-responsive embed-responsive-16by9">
                <iframe class="embed-responsive-item" :src="videoUrl"></iframe>
            </div>
            <h4>{{video.snippet.title}}</h4>
            <p>{{video.snippet.description}}</p>
        </div>
         <h3 v-else>Search video and select videolist plis!!</h3>
    </div>
</template>

<script>
    export default {
        name: 'VideoDetail',
        props:['video'],
        computed:{
            videoUrl(){
                let {videoId}= this.video.id;
                return `https://www.youtube.com/embed/${videoId}`;
            }
        }
    }
</script>

<style lang="css" scoped>
    .details{
        margin-right: 15px;
        padding: 10px;
        border: 1px solid black;
        border-radius: 4px;
    }
</style>
