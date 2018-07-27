<template>
  <div class="article">
    <div class="posts">
      <h1>{{post.title}}</h1>
    </div>
  </div>

</template>

<script>
export default {
  name: 'Article',
  data() {
    return {
      isLoading: false,
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
            this.isloading = false
            this.post = res.data.data
            console.log(this.post)
          }
        })
        .catch(err => {
          console.log(err)
        })
    }
  },
  beforeMount() {
    this.isLoading = true
    this.getAritleData()
  },
  watch: {
    $route(to, from) {
      his.getAritleData()
    }
  }
}
</script>

<style lang="scss" scoped>
.article {
  background-color: #e1e1e1;
  padding-top: 10px;
  .posts {
    width: 85%;
    margin-left: auto;
    margin-right: auto;
    border-radius: 3px;

    background: #fff;
  }
  h1 {
    font-size: 22px;
    font-weight: 700;
    margin: 8px 0;
    display: inline-block;
    vertical-align: bottom;
    width: 75%;
    line-height: 130%;
  }
}
</style>
