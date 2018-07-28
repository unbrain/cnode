<template>
  <div class="header clearfix">
    <router-link :to="{name: 'root'}"><img src="https://o4j806krb.qnssl.com/public/images/cnodejs_light.svg" alt=""></router-link>
    <ul>
      <li>
        <router-link :to="{name: 'root'}"><a href="#">首页</a></router-link>
        
      </li>
      <li>
        <a href="#">新手入门</a>
      </li>
      <li>
        <a href="#">API</a>
      </li>
      <li>
        <a href="#">关于</a>
      </li>
      <li>
        <a href="#">注册</a>
      </li>
      <li>
        <a href="#">登录</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style lang="scss" scoped>
.header {
  padding: 10px 120px;
  background: #444444;
  img {
    width: 120px;
    height: 30px;
  }
  .clearfix::after {
    content: '';
    display: block;
    clear: both;
  }
  ul {
    float: right;
  }
  li {
    line-height: 30px;
    list-style: none;
    display: inline-block;
    padding-right: 30px;
  }
  a {
    list-style: none;
    text-decoration: none;
    color: #cccccc;
  }
  a:hover {
    color: #fff;
  }
  a:focus {
    color: #3f82c4;
  }
}
</style>
