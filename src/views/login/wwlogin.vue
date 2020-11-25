<template>
  <div class=" login-container">
    <div id="wechat_login"></div>
  </div>
</template>

<script>
import { getWwConfig } from '@/api/user'

export default {
  name: 'Wwlogin',
  created: function() {
    getWwConfig().then((data) => {
      window.WwLogin({
        'id': 'wechat_login',
        'appid': data.corpid,
        'agentid': data.agentid,
        'redirect_uri': data.redirect_uri,
        'state': data.state
      })
    }).catch((err_res) => {
      console.log('get login meta false') // Error
      this.$alert(err_res.body, '获取企业信息失败', {
        confirmButtonText: '确定'
      })
    })
  }
}
</script>

<style scoped>
.login-container {
  /*box-shadow: 0 0px 8px 0 rgba(0, 0, 0, 0.06), 0 1px 0px 0 rgba(0, 0, 0, 0.02);*/
  -webkit-border-radius: 5px;
  border-radius: 5px;
  -moz-border-radius: 5px;
  background-clip: padding-box;
  margin: 180px auto;
  width: 450px;
  padding: 35px 35px 15px 35px;
  background: #fff;
  border: 1px solid #eaeaea;
  box-shadow: 0 0 25px #cac6c6;
}
</style>
