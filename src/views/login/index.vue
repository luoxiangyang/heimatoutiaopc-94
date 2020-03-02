<template>
 <div class="login">
     <el-card class='login-card'>
         <div class="imgs">
             <img src="../../assets/img/logo_index.png" alt="">
         </div>
         <!-- 表单 -->
         <el-form>
             <el-form-item>
                 <el-input style="margin-top:30px" placeholder="请输入手机号"></el-input>
             </el-form-item>
             <el-form-item>
                 <el-input style="width:60%" placeholder="请输入验证码"></el-input>
                 <el-button style="float:right " plain>验证码</el-button>
             </el-form-item>
            <el-form-item>
                <el-checkbox>我已阅读同意用户协议和隐私条款</el-checkbox>
            </el-form-item>
            <el-form-item>
                <el-button style="width:100%" type="primary">登录</el-button>
            </el-form-item>

         </el-form>
     </el-card>
 </div>
</template>

<script>
export default {

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
