<template>
    <div class="container">
      <div class="col-sm-12 text-center">
        <div>
          <h3> {{ place }} </h3>
          <h3> District - {{district}}</h3>
        </div>
    </div>
    <div class="col-sm-12">
      <div class="row">
        <div class="col-lg-3 col-sm-6 place-photo" v-for="(url,idx) in imgUrls"  v-show="idx>showPhotosLimit ? false: true">
          <a :href="url"><img :src="url" height="200px" width="250px"></a>
        </div>

        <div class="col-sm-12">
          <div class="row">
          <div class="col-md-6">
            <button type="button" class="btn btn-primary" @click="loadMorePhotos">View More Photos</button>
          </div>
          <div v-show="imageLoaded" class="col-md-6">
            <div class="square-spinner"></div>
          </div>
        </div>
        </div>
      </div>
    </div>

    <place-comment></place-comment>
  </div>
</template>


<script>
  import Comment from './Comments.vue';
  export default {
    data : function(){
      return{
        place: 'Bageshwar',
        district: 'Bageshwar',
        showPhotosLimit : 3,
        imageLoaded : false,
        imgUrls : [
          'http://www.uttarakhandtraveller.com/media/uploaded/Nainital_lake_NBhQczc27b9a8d6.jpg',
          'http://www.uttarakhandtraveller.com/media/uploaded/Nainital_lake_wvFdAVrdwqTCOIt.jpg',
          'http://www.uttarakhandtraveller.com/media/uploaded/Nainital_and_outskirts._Snaps_from_Dec_2017_36kVvlOTv0eR4ye.jpg',
          'http://www.uttarakhandtraveller.com/media/uploaded/Nainital_and_outskirts._Snaps_from_Dec_2017_HntIVog2nNCisTL.jpg',
          'http://www.uttarakhandtraveller.com/media/uploaded/Nainital_and_outskirts._Snaps_from_Dec_2017_ZtXW1uk3Adj50EN.jpg',
          'http://www.uttarakhandtraveller.com/media/uploaded/Nainital_and_outskirts._Snaps_from_Dec_2017_BbVjAtQ9qRgv5S7.jpg',
          'http://www.uttarakhandtraveller.com/media/uploaded/nainital_Nij6UtBsbxuDgAv.jpg',
          'http://www.uttarakhandtraveller.com/media/uploaded/Nainital_rXlj0MNlMH75vgl.jpg',
          'http://www.uttarakhandtraveller.com/media/uploaded/Nainital_MSfiFK0RjRTugID.jpg',
          'http://www.uttarakhandtraveller.com/media/uploaded/Nainital_2lLIsmj0B2ndd8T.jpg'
        ]
      }
    },
    components:{
      placeComment: Comment
    },
    computed: {

    }
    ,
    methods: {
      loadMorePhotos(){
        if(this.showPhotosLimit >= this.imgUrls.length){
          return;
        }
        this.imageLoaded = true;
        var vm = this;
        setTimeout(function(){
           vm.imageLoaded = false;
           vm.showPhotosLimit+=4;
         }, 2000);
      }
    }
  }
</script>

<style>
.place-photo{
  border-style: outset;
}

.square-spinner {
    width: 55px;
    display: block;
    background-color: #03A9F4;
    height: 55px;
    -webkit-animation: 3s rotate2 ease-in-out infinite;
    animation: 3s flip ease-in-out infinite;
}

@-webkit-keyframes flip {
    0% {
    -webkit-transform: perspective(120px) rotateX(0deg) rotateY(0deg);
    transform: perspective(120px) rotateX(0deg) rotateY(0deg);
    }
    25% {
    -webkit-transform: perspective(120px) rotateX(-180deg) rotateY(0deg);
    transform: perspective(120px) rotateX(-180deg) rotateY(0deg);
    }
    50% {
    transform: perspective(120px) rotateX(-180deg) rotateY(-180deg);
    -webkit-transform: perspective(120px) rotateX(-180deg) rotateY(-180deg);
    }
    75% {
    -webkit-transform: perspective(120px) rotateX(0deg) rotateY(-180deg);
    transform: perspective(120px) rotateX(0deg) rotateY(-180deg);
    }
    100% {
    -webkit-transform: perspective(120px) rotateX(0deg) rotateY(-360deg);
    transform: perspective(120px) rotateX(0deg) rotateY(-360deg);
    }
}

@keyframes flip {
    0% {
    -webkit-transform: perspective(120px) rotateX(0deg) rotateY(0deg);
    transform: perspective(120px) rotateX(0deg) rotateY(0deg);
    }
    25% {
    -webkit-transform: perspective(120px) rotateX(-180deg) rotateY(0deg);
    transform: perspective(120px) rotateX(-180deg) rotateY(0deg);
    }
    50% {
    transform: perspective(120px) rotateX(-180deg) rotateY(-180deg);
    -webkit-transform: perspective(120px) rotateX(-180deg) rotateY(-180deg);
    }
    75% {
    -webkit-transform: perspective(120px) rotateX(0deg) rotateY(-180deg);
    transform: perspective(120px) rotateX(0deg) rotateY(-180deg);
    }
    100% {
    -webkit-transform: perspective(120px) rotateX(0deg) rotateY(-360deg);
    transform: perspective(120px) rotateX(0deg) rotateY(-360deg);
    }
}



</style>
