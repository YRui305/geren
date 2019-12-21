<template>
  <div class="login">
    <!-- 放置一个el-card组件 -->
    <el-card class="login-card">
      <div class="title">
        <img src="../../assets/img/logo_index.png" alt="">
      </div>
      <!-- 放置表单 -->
      <el-form ref="myForm" :model="loginForm" :rules="loginRules" style="margin-top:20px">
        <!-- 表单域里面 prop要写要检验的字段名 放置 input/select/chechbox相当于一行 -->
        <el-form-item prop="mobile">
          <el-input v-model="loginForm.mobile" placeholder="请输入手机号"></el-input>
        </el-form-item>
        <!-- 表单域里面内容 -->
        <el-form-item prop="code">
          <el-input v-model="loginForm.code" style="width:60%" placeholder="请输入验证码"></el-input>
          <el-button style="float:right" plain>发送验证码</el-button>
        </el-form-item>
        <!-- 复选框 -->
        <el-form-item prop="check">
          <el-checkbox v-model="loginForm.check"> 我已阅读并同意用户协议和隐私条款</el-checkbox>
        </el-form-item>
        <el-form-item>
          <el-button @click="submitiLogin" type="primary" style="width:100%">登录</el-button>
        </el-form-item>
        <!-- <el-form-item>
          <el-button type="primary" style="width:100%">登录</el-button>
        </el-form-item> -->
      </el-form>
    </el-card>
  </div>
</template>

<script>
export default {
  data () {
    return {
      loginForm: {
        mobile: '', // 手机号
        code: '', // 验证码
        check: false // 是否勾选
      },
      loginRules: {
        // 验证规则对象，key（字段名）：value=》（）
        mobile: [{ required: true, message: '请输入您的手机号' },
          { pattern: /^1[3456789]\d{9}$/, message: '请输入合法的手机号' }],
        code: [{ required: true, message: '请输入验证码' },
          { pattern: /^\d{6}$/, message: '验证码为6位数字' }],
        check: [{ validator: function (rule, value, callback) {
          // 自定义校验函数
          if (value) {
            callback()// 认为当前规则检校通过
          } else {
            callback(new Error('请选择同意'))// 如果没有勾选
          }
        } }]
        // chek: [{ require: true, message: '请选择同意' }]
      }
    }
  },
  methods: {
    submitiLogin () {
      // 手动校验
      this.$refs.myForm.validate((isok) => {
        if (isok) {
          // 校验通过，点用登录接口
          // console.log('检校通过，开始登陆')
          this.$axios({
            url: '/authorizations', // 请求axios没有指定类型
            method: 'post', // 类型
            data: this.loginForm//
          }).then(result => {
            window.localStorage.setItem('user-token', result.data.token)
            console.log(result.data.token)
          }).catch(() => {

          })
        }
      })
    }
  }

}
</script>

<style lang='less' scoped>
  .login{
    background-image: url(../../assets/img/5.jpg);
    height: 100vh;
    background-size: cover;//自适应覆盖
    display: flex;
    justify-content: center;
    align-items: center;

    .login-card {
      width:400px;
      height:320px;
      .title{
        text-align: center;
        margin-bottom: 20px;
        img{
          height: 40px;
        }
      }
    }
  }

</style>
