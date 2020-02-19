<template>
  <div class="login_con">
    <div class="login_box">
      <!-- 头像区域 -->
      <div class="avatar_box">
        <img src="../assets/logo.png" alt />
      </div>
      <!-- <div class="input_box">
        <input type="text" />
        <br />
        <br />
        <input type="text" />
      </div>-->

      <!-- 登录表单区域 -->
      <el-form class="login_from"  status-icon="true" :rules="rules" :model="form" ref="loginformref" label-width="px">
        <!-- 用户名 -->
        <el-form-item prop="name" label>
          <el-input v-model="form.name" placeholder="请输入用户名" prefix-icon="el-icon-user-solid"></el-input>
        </el-form-item>
        <!-- 密码 -->
        <el-form-item prop="region" label>
          <el-input v-model="form.region" prefix-icon="el-icon-star-on" show-password></el-input>
        </el-form-item>
        <!-- 按钮 -->
        <el-form-item class="login_button">
          <el-button type="primary" @click="validate">登录</el-button>
          <el-button type="info" @click="reset">重置</el-button>
        </el-form-item>
      </el-form>

      <!-- <div class="button_box">
        <button>登录</button>
        <button>重置</button>
      </div>-->
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      form:{
        name: '',
        region: ''
      },
      rules: {
          name: [
            { required: true, message: '请输入用户名', trigger: 'blur' },
            { min: 8, max: 15, message: '长度在 8 到 15 个字符', trigger: 'blur' }
          ],
          region: [
            { required: true, message: '请输入密码', trigger: 'change' }
          ],
      }
    }
  },

  methods:{
    reset(){
        this.$refs.loginformref.resetFields();
    },
    validate(){
       this.$refs.loginformref.validate(async valid => {
          
          if(!valid)  return this.$message.error('log error')
          this.$message.success('log success')

          // window.sessionStorage.setItem("token", res.data.token);

          this.$router.push('/home')
        
          // const {data: res} = await this.$http.post('login', this.form)
          // if(res.meta.status !==200) return alert('登录失败')

       })  
    }  
  }
};
</script>


<style  scoped>
.login_button {
  display: flex;
}
.login_con {
  background-color: #2b4b6b;
  height: 100%;
}

.login_box {
  width: 450px;
  height: 300px;
  background-color: #fff;
  border-radius: 3px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

.avatar_box {
  width: 130px;
  height: 130px;
  border: 8px solid whitesmoke;
  border-radius: 50%;
  background-color: #fff;

  position: absolute;
  left: 35%;

  margin-top: -80px;
}

.avatar_box img {
  margin-top: 25px;
  width: 120px;
  height: 100px;
}

.input_box {
  /* border: 1px solid red; */
  position: absolute;
  width: 400px;
  left: 30px;
  bottom: 100px;
}

.input_box input {
  border: gray 1px solid;
  height: 30px;
  width: 380px;

  margin-left: -10px;
  padding-left: 30px;

  background-image: url("../assets/target.jpg");
  background-repeat: no-repeat;
  background-position: 1% center;
  background-size: 5%;
}

.button_box {
  height: 30px;
  width: 100px;
  /* border: 1px solid red; */

  position: absolute;
  right: 30px;
  bottom: 30px;
}

.login_from {
  position: absolute;
  bottom: 0;
  width: 100%;
  /* border: 1px solid red; */

  padding: 0 20px;
  box-sizing: border-box;
}

.login_button {
  display: flex;
  justify-content: flex-end;
}
</style>