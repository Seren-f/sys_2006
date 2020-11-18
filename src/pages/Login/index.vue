<template>
 <div id="container">
    <div class="left"></div>
    <div class="right">
      <h1>千锋管理系统</h1>
      <div class="login-page">
    <el-form :model="loginForm" status-icon :rules="rules" ref="loginForm" label-width="100px" class="demo-loginForm">
      <el-form-item label="用户名" prop="username">
        <el-input type="text" v-model="loginForm.username" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="密码" prop="password">
        <el-input type="password" v-model="loginForm.password" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="submitForm('loginForm')">提交</el-button>
      </el-form-item>
    </el-form>
  </div>
    </div>
    <video class="bg_video" muted
           src="../../assets/video/video.mp4"
           autoplay
           loop
           preload="auto"></video>
 </div>
</template>

<script>
  export default {
    data() {
      // jsDoc
      /**
       * @param {Object} rule 就是一个表单验证对象
       * @param {String} value 输入值
       * @param {Function} callback 校验通过不传参 不通过传参
      */
      var validateUsername = (rule, value, callback) => {
        //用户名正则，4到16位(字母、数字、下划线、减号)
        // var uPattern=/^[a-zA-Z0-9_-]{4,16}$/;
        if(!value){
          callback('4到16位(字母、数字、下划线、减号)')
        }else{
          callback()
        }

      };
      var validatePassword = (rule, value, callback) => {
        if(!value){
          callback('请输入密码')
        }else{
          callback()
        }
      };
      return {
        loginForm: {
          username: '',
          password: ''
        },
        rules: {
          username: [
            { validator: validateUsername, trigger: 'blur' }
          ],
          password: [
            { validator: validatePassword, trigger: 'blur' }
          ]
        }
      };
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {//代表本地校验通过
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
  }
</script>
<style scoped>
  /* 表单样式 */
  .el-form{
    width:400px ;
  }
   .right{
    position:absolute;
    top:120px;
    right: 40px;
    z-index: 10;
    height: 60%;
    background: rgba(0, 0, 0, 0.2);
    border-radius: 10px;
  }
  .right h1{
    color: #fff;
    margin-top: 100px;
    margin-bottom: 50px;
    text-align: center;
  }
      .el-button.el-button--primary {
      width: 250px;
      background: linear-gradient(90deg, #1596fb, #002dff);
    }

</style>
