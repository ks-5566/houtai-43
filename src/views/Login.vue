<template>
<div class="banxin">
  <el-form  ref="form" :model="form" label-width="80px" :rules="rules" class="one">
  <el-form-item label="账号" prop="username">
    <el-input v-model="form.username"></el-input>
  </el-form-item>
  <el-form-item label="密码" prop="password">
    <el-input v-model="form.password" type="password"></el-input>
  </el-form-item>
  <el-form-item>
    <el-button type="primary" @click="onSubmit">登录</el-button>
    <el-button>取消</el-button>
  </el-form-item>
</el-form>
</div>
</template>

<script>
export default {
  data(){
      return{
          // 表单的数据对象
          form:{
              username:"",
              password:""
          },
          rules: {
          username: [
            { required: true, message: '请输入手机号码', trigger: 'blur' },
            { min: 11, max: 11, message: '手机号码格式错误', trigger: 'blur' },
          ],
          password:[
                { required: true, message: '请输入密码', trigger: 'blur' },
          ],
        }
      };
  },
  methods: {
      onSubmit() {
          this.$refs.form.validate(valid=>{
              if(valid){
                //   提交表单登录
                this.$axios({
                    url:"/login",
                    method:"POST",
                    data:this.form
                }).then(res=>{
                //  data是用户的数据，里面包含token和user的信息
                const {data}=res.data;
                // 判断当前用户是否有权限
                if(data.user.role.type !=="admin"){
                    this.$message({
                        message:"权限不够，必须是管理员",
                        type:"warning"
                    });
                    return;
                }
                // 转换成字符串
                const userStr=JSON.stringify(data);
                // 保存到本地，可以给其他按钮使用
                localStorage.setItem('userInfo',userStr)
                // 登录成功的提示
                this.$message({
                     message:"登录成功",
                     type:'success'
                  });
                  this.$router.push("/index")
                })
              }
          });
       }
    }
 };
</script>

<style scoped lang="less">
 .banxin{
     display:flex;
     justify-content: center;
     align-items: center;
     text-align: center;
     height: 120vh;
 }
  
  .one{
      width: 400px;
  }
</style>