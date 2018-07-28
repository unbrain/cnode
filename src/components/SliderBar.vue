<template>
  <div class="autherinfo">
    <div class="authersummay">
      <div class="topbar">作者 {{this.$route.params.name}}</div>
      <router-link :to="{
          name:'user_info',
          params:{
            name:userData.loginname
          }
          }">
        <img :src="userData.avatar_url" alt="">
      </router-link>
      <p>
        积分: {{userData.score}}
      </p>
    </div>
    <div class="recent_topics">
      <div class="topbar">作者最近主题</div>
      <ul>
        <li v-for="list in topic5">
          <router-link :to="{
        name:'post_content',
        params:{
          id:list.id,
          name:list.author.loginname
        }
        }">
            {{list.title}}
          </router-link>
        </li>
      </ul>
    </div>
    <div class="recent_replies">
      <div class="topbar">作者最近回复</div>
      <ul>
        <li v-for="list in reply5">
          <router-link :to="{
        name:'post_content',
        params:{
          id:list.id,
          name:list.author.loginname
        }
        }">
            {{list.title}}
          </router-link>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  name: 'SliderBar',
  data() {
    return {
      userData: {}
    }
  },
  methods: {
    getUserData() {
      this.Axios.get(
        `https://cnodejs.org/api/v1/user/${this.$route.params.name}`
      )
        .then(res => {
          this.userData = res.data.data
          console.log(this.userData)
        })
        .catch(err => {
          console.log(err)
        })
    }
  },
  computed: {
    topic5() {
      if (this.userData.recent_topics) {
        return this.userData.recent_topics.slice(0, 5)
      }
    },
    reply5() {
      if (this.userData.recent_replies) {
        console.log(this.userData.recent_replies.slice(0, 5))
        return this.userData.recent_replies.slice(0, 5)
      }
    }
  },
  beforeMount() {
    this.getUserData()
  }
}
</script>

<style lang="scss" scoped>
.authersummay,
.recent_replies,
.recent_topics {
  background-color: #fff;
  p {
    padding: 5px 10px;
  }
}
.autherinfo {
  width: 328px;
  float: right;
  margin: 15px;
}
li {
  padding: 3px 0;
}
.recent_replies ul,
.recent_topics ul {
  margin-top: 0px;
  margin-bottom: 0px;
  list-style: none;
  padding-left: 14px;
}

ul a {
  font-size: 12px;
  text-decoration: none;
  color: #778087;
}

.topbar {
  padding: 10px;
  background-color: #f6f6f6;
  font-size: 12px;
  margin-top: 10px;
}

img {
  height: 48px;
  width: 48px;
  border-radius: 3px;
  margin: 10px;
}

.loginname {
  width: 100px;
  float: right;
  margin-top: 22px;
  margin-right: 159px;
  font-size: 14px;
}

.loginname a {
  text-decoration: none;
  color: #778087;
}

.authersummay .topbar {
  margin-top: 0px;
}
</style>
