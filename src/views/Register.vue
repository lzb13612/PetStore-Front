<template>
  <el-row style="height: 100%;">
    <el-col :span="8" :offset="8" style="border-style: solid;border-color: #e6e6e6;margin-top: 5%">

      <el-row>
        <el-col :span="16" :offset="4">
          <el-form>
            <h3>注册界面</h3>
            <el-form-item label="账户地址">
              <el-input type="primary" v-model="address" @click="register"></el-input>
            </el-form-item>
          </el-form>
        </el-col>
      </el-row>
      <el-row>
        <el-button type="primary" @click="register">注册</el-button>
        <el-button type="primary" @click="goback">返回</el-button>
      </el-row>
    </el-col>

  </el-row>

</template>

<script>
export default {
  data(){
    return{
      address:"",
    }
  },
  name: "Register",
  methods: {
    register: function () {
      this.axios.get(`user/register?address=${this.address}`).then((response)=>{
        console.log(response.data.result)
        if(response.data.code === 1){
          console.log(response.data.result)
          alert("注册成功")
          this.$router.push('/login')
        }else {
          console.log(this.address)
          this.address = ''
          alert(response.data.result)
        }
      })
    },
    goback: function () {
      this.address = ''
      this.$router.push('/login')
    }

  }
}
</script>

<style scoped>

</style>
