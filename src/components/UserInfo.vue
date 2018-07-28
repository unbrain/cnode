<template>
  <div>
    <div class="userInfomation">
      <section>
        <img :src="post.avatar_url">
        <span>{{post.loginname}}</span>
        <p>
          {{post.score}}积分
        </p>
        <p>
          注册时间：{{post.create_at | formatDate}}
        </p>
      </section>
      <div class="topics">
        <p>最近创建的话题</p>
        <ul>
          <li v-for="item in post.recent_topics">
            <!--头像-->
            <img :src="item.author.avatar_url" alt="">
            <!--回复/浏览-->
            <span class="allcount">
              <span class="reply_count">{{item.reply_count}}</span>
              /{{item.visit_count}}
            </span>

            </span>
            <!--标题-->
            <router-link :to="{
        name:'post_content',
        params:{
          id:item.id,
          name:item.author.loginname
        }
        }">
              <span>
                {{item.title}}
              </span>
            </router-link>
            <!--最終回复时间-->
            <span class="last_reply">
              {{post.last_reply_at | formatDate}}
            </span>
          </li>
        </ul>
      </div>
      <div class="replies">
        <p>最近参与的主题</p>
        <ul>
          <li v-for="item in post.recent_replies">
            <!--头像-->
            <img :src="item.author.avatar_url" alt="">
            <!--回复/浏览-->
            <span class="allcount">
              <span class="reply_count">{{item.reply_count}}</span>
              /{{item.visit_count}}
            </span>

            </span>
            <!--标题-->
            <router-link :to="{
        name:'post_content',
        params:{
          id:item.id,
          name:item.author.loginname
        }
        }">
              <span>
                {{item.title}}
              </span>
            </router-link>
            <!--最終回复时间-->
            <span class="last_reply">
              {{post.last_reply_at | formatDate}}
            </span>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'UserInfo',
  data() {
    return {
      post: []
    }
  },
  methods: {
    getUserData() {
      this.Axios.get(
        `https://cnodejs.org/api/v1/user/${this.$route.params.name}`
      )
        .then(res => {
          this.post = res.data.data
          console.log(this.post.recent_topics)
        })
        .catch(err => {
          console.log(err)
        })
    }
  },
  beforeMount() {
    this.getUserData()
  }
}
</script>
<style lang="scss">
.userInfomation {
  background: white;
  width: 75%;
  margin: 10px auto;
}
.userInfomation section {
  padding: 12px;
}
.userInfomation img {
  width: 30px;
}
.userInfomation li {
  list-style: none;
}
.userInfomation .replies,
.userInfomation .topics {
  font-size: 0.72rem;
  border-top: 10px #dddddd solid;
}
.userInfomation > div > p {
  padding: 12px 0 12px 12px;
  background-color: rgba(212, 205, 205, 0.17);
  font-size: 0.75rem;
  margin: 0;
}
.userInfomation > div > ul > li {
  padding: 4px 0 4px 12px;
  white-space: nowrap;
  font-size: 0.72rem;
  text-overflow: ellipsis;
  overflow: hidden;
  line-height: 30px;
  vertical-align: middle;
}
.userInfomation > div > ul > li > a {
  color: #094e99;
  text-decoration: none;
}
p {
  color: #a1a1a1;
}
</style>
