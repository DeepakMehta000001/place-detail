<template>
  <div class="comments-section">
    <div class="form-group">
      <label for="comment" style="margin-top:10px;">Comment:</label>
      <textarea class="form-control" v-model="message" rows="2" id="comment"></textarea>
      <div class="col-sm-12">
        <button type="button" class="btn pull-right btn-primary" @click="addComment($event)">Submit</button>
      </div>
      <div class="col-sm-12" v-for="comment in commentList">
        <h4 class="comment-style" style="white-space: pre-line;">{{ comment }}</h4>
      </div>
    </div>
  </div>
</template>

<script>
  export default{
    data: function(){
      return {
        message : "",
        commentList : []
      }
    },
    methods: {
      addComment(){
        if(this.message.length == 0){
          return;
        }
        var currentdate = new Date();
        var datetime =  currentdate.getDate() + "/"
                        + (currentdate.getMonth()+1)  + "/"
                        + currentdate.getFullYear() + "  "
                        + currentdate.getHours() + ":"
                        + currentdate.getMinutes() + ":"
                        + currentdate.getSeconds();
        this.commentList.push(datetime+":  "+this.message);
        this.message = "";
      }
    }
  }
</script>

<style>
.comment-style{
  background-color: #DCDCDC;
  line-height: 30px;
}
</style>
