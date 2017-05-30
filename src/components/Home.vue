<template>
  <div class="home">
    <!-- YOU WILL PROBABLY END UP WITH SOMETHING LIKE THIS -->
    <h1 class="title">Live for Music</h1>
    <div class="container-fluid">
      <div class="row">
        <div class="col-sm-6">
          <itunes class="itunes"></itunes>
        </div>
        <div class="col-sm-6">
          <mytunes class="mytunes"></mytunes>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import Mytunes from './Mytunes'
  import Itunes from './Itunes'
  export default {
    name: 'home',
    components: {
      Itunes,
      Mytunes
    },
    data() {
      return {

      }
    }
  }

</script>


<style>
  /**
* YOU SHOULD PROBABLY MAKE THIS LOOK BETTER :)
* BOOTSTRAP IS FOR THE WEAK FLEXBOX IS KING
* -- McCall
**/
  
  body {
    background-image: url("https://images2.alphacoders.com/701/thumb-1920-70172.jpg");
    background-position: center center;
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-size: cover;
  }
  
  h1 {
    font-family: Niconne;
    font-size: 80px;
    font-style: normal;
    font-variant: normal;
    font-weight: 500;
    line-height: 26.4px;
    text-align: center;
    color: whitesmoke;
    margin-bottom: 35px
  }
</style>