<template>
    <div class="header clearfix">
        <img src="https://o4j806krb.qnssl.com/public/images/cnodejs_light.svg" alt="">
        <ul>
            <li>
                <a href="#">首页</a>
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
    height: 40px;
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
    line-height: 40px;
    list-style: none;
    display: inline-block;
    padding-right: 30px;
  }
  a {
    list-style: none;
    text-decoration: none;
    color: #cccccc;
  }
}
</style>
