<template>
  <div class="article-con">
    <div class="article" id="content">
      <div class="topic_header">
        <div class="topic_title">
          <div class="topic_title">
            {{post.title}}
          </div>
          <ul>
            <li>• 发布于 {{post.create_at | formatDate}}</li>
            <li>• 作者 {{this.$route.params.name}}</li>
            <li>• {{post.visit_count}} 次浏览</li>
            <li>• 来自 {{post.tab | tabFormat}}</li>
          </ul>
          <div v-html="post.content" class="topic_content"></div>
        </div>
        <div id="reply">
          <div class="topbar" v-if="">
            {{post.replies.length}} 回复
          </div>
          <div v-for="v, k in post.replies" class="replySec">
            <router-link :to="{
              name: 'user_info',
              params:{
                name: v.author.loginname
              }
            }"><img :src="v.author.avatar_url" alt=""></router-link>
            
            <span>{{v.author.loginname}}</span> {{k+1}}楼 {{v.create_at | formatDate}}
            <p v-html="v.content"></p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Article',
  data() {
    return {
      post: {}
    }
  },
  methods: {
    getAritleData() {
      this.Axios.get(
        `https://cnodejs.org/api/v1/topic/${this.$route.params.id}`
      )
        .then(res => {
          if (res.data.success == true) {
            this.post = res.data.data
          }
        })
        .catch(err => {
          console.log(err)
        })
    }
  },
  beforeMount() {
    this.getAritleData()
  },
  watch: {
    $route(to, from) {
      his.getAritleData()
    }
  }
}
</script>

<style lang="scss">
@import url('../assets/markdown-github.css');
.article-con {
  width: 100%;
  background: #e1e1e1;
}
.article {
  padding-top: 15px;
  margin-left: auto;
  width: 80%;
  margin-right: auto;
}
.topbar {
  padding: 10px;
  background-color: #f6f6f6;
  font-size: 12px;
  margin-top: 10px;
}

#reply,
.topic_header {
  background-color: #fff;
}

#reply {
  margin-top: 15px;
}

.replySec>a>img {
  width: 30px;
  height: 30px;
  position: relative;
  bottom: -9px;
}

#reply a,
#reply span {
  font-size: 13px;
  color: #666;
  text-decoration: none;
}
.replySec {
  border-bottom: 1px solid #e5e5e5;
  padding: 0 10px;
}

.loading {
  text-align: center;
  padding-top: 300px;
}

.replyUp a:nth-of-type(2) {
  margin-left: 0px;
  display: inline-block;
}

.topic_header {
  padding: 10px;
}

.topic_title {
  font-size: 20px;
  font-weight: bold;
  padding-top: 8px;
}

.topic_header ul {
  list-style: none;
  padding: 0px 0px;
  margin: 6px 0px;
}

.topic_header li {
  display: inline-block;
  font-size: 12px;
  color: #838383;
}

.topic_content {
  border-top: 1px solid #e5e5e5;
  padding: 0 10px;
}

.markdown-text img {
  width: 92% !important;
}
</style>
