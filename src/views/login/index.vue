<template>
 <div class="login">
     <el-card class='login-card'>
         <div class="imgs">
             <img src="../../assets/img/logo_index.png" alt="">
         </div>
         <!-- 表单 -->
         <el-form ref="loginForm" :model="loginForm" :rules="loginRules">
             <el-form-item prop="mobile">
                 <el-input v-model="loginForm.mobile" style="margin-top:30px" placeholder="请输入手机号"></el-input>
             </el-form-item>
             <el-form-item prop="code">
                 <el-input v-model="loginForm.code" style="width:60%" placeholder="请输入验证码"></el-input>
                 <el-button style="float:right" plain>验证码</el-button>
             </el-form-item>
            <el-form-item prop="checked">
                <el-checkbox v-model="loginForm.checked">我已阅读同意用户协议和隐私条款</el-checkbox>
            </el-form-item>
            <el-form-item>
                <el-button @click="login" style="width:100%" type="primary">登录</el-button>
            </el-form-item>

         </el-form>
     </el-card>
 </div>
</template>

<script>
export default {
  data () {
    return {
      loginForm: {
        mobile: '',
        code: '',
        checked: false
      },
      loginRules: {
        mobile: [{ required: true, message: '您的手机号不能为空' },
          { pattern: /^1[3-9]\d{9}$/, message: '您的手机号不正确' }],
        code: [{ required: true, message: '您的验证码不能为空' },
          { pattern: /^\d{6}$/, message: '您的验证码不正确' }],
        checked: [{
          validator: function (rule, value, callback) {
            value ? callback() : callback(new Error('您必须同意我们的条款'))
          }
        }]
      }
    }
  },
  methods: {
    login () {
      this.$refs.loginForm.validate().then(res => {
        this.$axios({
          url: '/authorizations',
          method: 'post',
          data: this.loginForm
        }).then(result => {
          // 在本地设置token
          window.localStorage.setItem('user-token', result.data.token)
          this.$router.push('/home')
        }).catch(result => {
          this.$message.error('用户名或密码错误')
        })
      })
    }
  }
}
</script>

<style lang="less" scoped>
.login {
    height: 100vh;
    background-image: url('../../assets/img/login_bg.jpg');
    display: flex;
    justify-content: center;
    align-items: center;
    .imgs {
        text-align: center;
        img {
            width: 200px;
        }
    }
    .login-card {
        width: 440px;
        height: 340px;

    }
}
</style>
