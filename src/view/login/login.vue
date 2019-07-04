<style lang="less">
  @import './login.less';
</style>


<template>
  <div class="login">
    <div class="login-con">
      <Row class="height-100">
        <Col span="16" class="height-100 login-bg">
          <div class="login-company" onselectstart="return false;">
            <img src="../../assets/images/logo.png" alt ondragstart="return false;">
            <span>一体化管理平台（OMP）</span>
          </div>
        </Col>
        <Col span="8" class="height-100" style="padding:50px;">
          <h2 class="h2-title">河南油田工程咨询股份有限公司</h2>
          <Card icon="log-in" :bordered="false" style="width:90%;margin:0 auto;">
            <h2 style="font-weight:600; color:black;padding-bottom:20px;">登 录 到 你 的 账 户</h2>
            <div class="form-con">
              <login-form @on-success-valid="handleSubmit"></login-form>
              <p class="login-tip"></p>
            </div>
          </Card>
          <div class="copy-right">
            <p>Copyright © 2019 河南油田工程咨询股份有限公司.All Rights Reserved</p>
            <p>技术支持单位：河南油田工程咨询股份有限公司</p>
            <p>支持电话：0371-53608335</p>
          </div>
        </Col>
      </Row>
    </div>
  </div>
</template>

<script>
import LoginForm from '_c/login-form'
import { mapActions } from 'vuex'
export default {
  components: {
    LoginForm
  },
  methods: {
    ...mapActions([
      'handleLogin',
      'getUserInfo'
    ]),
    handleSubmit ({ userName, password }) {
      this.handleLogin({ userName, password }).then(res => {
        this.getUserInfo().then(res => {
          this.$router.push({
            name: this.$config.homeName
          })
        })
      })
    }
  }
}
</script>

<style>

</style>
