<template>
    <div class="itunes">
        <div class="row">
            <div class="col-xs-12 text-center">
                <form @submit.prevent='search'>
                    <input v-model='query' placeholder="Artist" />
                    <button type='submit' class="btn btn-primary">Submit</button>
                </form>
            </div>
            <div class="col-xs-12">
                <div class="row">
                    <div v-for='song in songs' class="songlist col-xs-12">
                        <div class="well">
                            <div class="row">
                                <div class="col-xs-12">{{song.artistName}}</div>
                            </div>
                            <div class="row">
                                <div class="col-xs-12">{{song.collectionName}}</div>
                            </div>
                            <div class="row">
                                <div class="col-xs-12">
                                    <img :src='song.artworkUrl60' alt="">
                                </div>
                            </div>
                            <div class="row">
                                <div class="col-xs-12">{{song.trackName}}</div>
                            </div>
                            <div class="row">
                                <div class="col-xs-10">
                                    <audio controls>
                                        <source :src='song.previewUrl' type="audio/mpeg">
                                    </audio>
                                </div>
                                <div class="col-xs-2">
                                    <a @click='addTrack(song)' class='add-btn'><i class="material-icons" >add_circle_outline</i></a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
    import itunesService from '@/services/itunes-service/'
    import mytunesService from '@/services/mytunes-service/'
    export default {
        name: 'itunes',
        data() {
            return {
                query: '',
                songs: []

            }
        },
        computed: {},
        methods: {
            search: function () {
                itunesService.getMusicByArtist(this.query).then(res => {
                    let resObj = JSON.parse(res)
                    this.songs = resObj.results

                })
            },
            addTrack(song) {
                mytunesService.addTrack(song)
            }
        },
        components: {}
    }

</script>


<style scoped>
    .well {
        background-color: rgba(100, 100, 100, .1);
        text-align: center;
        color: whitesmoke
    }
    
    .add-btn {
        color: #c0c0c0;
    }
    .add-btn:hover {
        color: white;
        cursor: pointer
    }
</style>