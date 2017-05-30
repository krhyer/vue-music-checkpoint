<template>
    <div class="mytunes">
        <div class="row">

            <div class="col-xs-12 songlist m-t25" v-for='song in songs'>
                <div class="media">
                    <div class="media-left">
                        <img class="media-object" :src="song.artworkUrl60">
                        <p class="text-center">{{song.artistName}}</p>
                        <div class="votes">
                            <a @click='promoteTrack(song)'><i class="glyphicon glyphicon-chevron-up"></i></a>
                            <span>{{song.votes}}</span>
                            <a @click='demoteTrack(song)'><i class="glyphicon glyphicon-chevron-down"></i></a>
                        </div>
                    </div>
                    <div class="media-body">
                        <h4 class="media-heading">{{song.trackName}}</h4>
                        <p>{{song.collectionName}}</p>
                        <audio controls>
                            <source :src='song.previewUrl' type="audio/mpeg">
                        </audio>
                        <div class="btn-group">
                            <a class="text-danger" @click='removeTrack(song)'><i class="glyphicon glyphicon-trash"></i></a>
                        </div>
                    </div>
                </div>
                <!--<div class="well">
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
                            <div class="col-xs-4">
                                <audio controls>
                                    <source :src='song.previewUrl' type="audio/mpeg">
                                </audio>
                            </div>
                        </div>
                        <div class="row">
                            <div class="col-xs-2">
                            </div>
                        </div>
                    </div>-->
            </div>
        </div>
    </div>
</template>


<script>
    import mytunesService from '@/services/mytunes-service'
    export default {
        name: 'mytunes',
        data() {
            return {
                songs: mytunesService.getTracks()
            }
        },
        computed: {},
        methods: {
            removeTrack(song) {
                mytunesService.removeTrack(song)
            },
            getTracks() {
                this.songs = mytunesService.getTracks()
            },
            promoteTrack(song) {
                mytunesService.promoteTrack(song)
                this.getTracks()
            },
            demoteTrack(song) {
                mytunesService.demoteTrack(song)
                this.getTracks()                
            }
        },
        components: {}
    }

</script>


<style scoped>
    .media {
        color: whitesmoke
    }
    
    .m-t25 {
        margin-top: 25px
    }
    a:hover{
        cursor: pointer
    }
</style>