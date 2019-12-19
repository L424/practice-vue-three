<template>
  <div class="home">

    <div class="container">
      <div class="list">
        <ul class="list-group">
          <li class="list-group-item"
          v-for="(itme,index) in contentList"
          :key="index">
            <span>{{itme.title}}</span>
            <i class="fa fa-close"
            @click="del(itme.id)"></i>
          </li>
        </ul>
        <div class="input-group mb-3 form-todo">
          <input type="text" class="form-control" placeholder="Please enter todo">
          <div class="input-group-append">
            <button class="btn btn-outline-secondary" type="button" id="create-todo">创建</button>
          </div>
        </div>
      </div>
    </div>




    <div class="modal fade" id="deleteTodo" tabindex="-1" role="dialog" aria-labelledby="exampleModalCenterTitle" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalCenterTitle">提醒！</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            你确定你在干什么吗？
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">取消</button>
            <button type="button" class="btn btn-danger delete">确定删除</button>
          </div>
        </div>
      </div>
    </div>
<!--    <router-view v-if="isRouterAlive"></router-view>-->
  </div>

</template>
<script>
import axios from 'axios'
export default {
  name: 'home',
  // inject: ['reload'],
  data () {
    return {
      contentList: [],
        // isRouterAlive: true
    }
  },


  created() {
    axios({
      method: 'GET',
      url: 'http://localhost:3000/posts'
    }).then(res => {
      console.log(res)
      console.log(res.data)
      this.contentList = res.data
    })
  },
  components: {
  },
  methods:{
    del(id){
      axios({
        url: `http://localhost:3000/posts/${id}`,
        method: 'DELETE',
      }).then(()=> {
        // this.reload()
      })
    }
  }
}
</script>


<style lang="scss" scoped>
  .list {
    width: 300px;
    margin-top: 20px;
  }

  .list-group-item {
    border-color: #0c8ed9;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .list .list-group-item i {
    cursor: pointer;
    transition: .3s;
  }

  .list .list-group-item i:hover {
    transform: rotate(90deg) scale(1.2);
  }

  .form-todo {
    margin: 20px 0;
  }
</style>
