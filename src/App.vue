<template>
  <div id="app1">
      <SearchBar @termChange="termChange"></SearchBar>
      <app-video-detail :video="selectedVideo"></app-video-detail>
      <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
      <app-footer></app-footer>
  </div>
</template>

<script>
    import axios from 'axios';
    import SearchBar from './components/SearchBar.vue';
    import VideoList from './components/VideoList.vue';
    import Footer from './components/Footer.vue';
    import VideoDetail from './components/VideoDetail.vue';



    const API_KEY = 'AIzaSyBjJrOx9SDdqcNO_IJGY1rS-j-K1_uRwgY'
    export default {
        name: 'App',
        data(){
            return{
                videos:[],
                selectedVideo:null
            }
        },
        components:{
            SearchBar,
            VideoList,
            appFooter: Footer,
            appVideoDetail: VideoDetail
        },
        methods:{
            onVideoSelect(video){
                // console.log('video', video);
                this.selectedVideo = video;
            },
                termChange(eventDariSearchBar){
                    // liat doc https://www.googleapis.com/youtube/v3
                    axios.get('https://www.googleapis.com/youtube/v3/search',{
                        params:{
                            key: API_KEY,
                            type:'video',
                            part: 'snippet',
                            q:eventDariSearchBar
                        }
                    }).then(response => {
                        // console.log(response);
                        this.videos = response.data.items;
                    })
                }
        },
        computed:{
            showData(){
                return this.input
            }
        }
    }
</script>

<style scoped="">
    #app1{
        width: 80%;
        padding-top: 50px;
        margin: 0 auto;

        display: grid;
        grid-template-columns: 4fr 2fr;
        grid-template-rows: minmax(40px, 50px) minmax(300px,1fr) minmax(40px, 50px);
        grid-template-areas: "search search"
                             "showVideo listVideo"
                             "footer footer";
    }
    .search-bar{
        grid-area: search;
    }
    .list__items{
        grid-area: listVideo;
    }
    .footer{
        grid-area: footer;
    }
    .video{
        grid-area: showVideo;
    }
</style>
