<template>
  <div>
    <div class="app-header">
      <div class="app-header-inner">
        <router-link :to="{path: '/'}">
          <img src="../assets/logo.png" alt="" class="head-logo">
        </router-link>
        <div class="header-nav">
          <ul class="nav-list">
            <li>{{username}}</li>
            <li v-if="username!==''" class="nav-pile">|</li>
            <li v-if="username!==''" @click="quit">退出</li>
            <li v-if="username===''" @click="logClick">登录</li>
            <li class="nav-pile">|</li>
            <li v-if="username===''" @click="regClick">注册</li>
            <li v-if="username===''" class="nav-pile">|</li>
            <li @click="aboutClick">关于</li>
          </ul>
        </div>
      </div>
    </div>
    <div class="app-content">
      <keep-alive>
        <router-view></router-view>
      </keep-alive>
    </div>
    <div class="app-footer">
      <p>@ 2016 fishenal MIT</p>
    </div>
    <my-dialog :is-show="isShowAboutDialog" @on-close="closeDialog('isShowAboutDialog')">
      <p>本报告在调研数据的基础上，采用定性与定量相结合的方式深入
      分析了火热的开发和私人飞机上的恢复而复活丢分地方交话费和
      发货人缴费和优惠</p>
    </my-dialog>
    <my-dialog :is-show="isShowLogDialog" @on-close="closeDialog('isShowLogDialog')">
      <log-form @has-log="onSuccessLog"></log-form>
    </my-dialog>
    <my-dialog :is-show="isShowRegDialog" @on-close="closeDialog('isShowRegDialog')">
      <reg-form></reg-form>
    </my-dialog>
  </div>
</template>
<script>
  import Dialog from './base/dialog'
  import LogForm from './logForm'
  import RegForm from './regform'
  export default{
    components:{
      MyDialog:Dialog,
      LogForm,
      RegForm
    },
    data(){
      return{
        isShowAboutDialog:false,
        isShowLogDialog:false,
        isShowRegDialog:false,
        username:""
      }
    },
    methods:{
      aboutClick(){
        this.isShowAboutDialog=true
      },
      logClick(){
        this.isShowLogDialog=true
      },
      regClick(){
        this.isShowRegDialog=true
      },
      closeDialog(attr){
        this[attr]=false
      },
      onSuccessLog(data){
        this.closeDialog('isShowLogDialog')
        this.username=data.username
      },
      quit(){
        this.username=''
      }
    }
  }
</script>
<style >
*{
	margin: 0;
	padding: 0;
}
.clearfix:after{
	display: block;
	height: 0;
	content: '';
	clear: both;
	visibility: hidden;
}
ul,li,ol,dl,dt,dd,p,h1,h2,h3,h4,h5,h6,label,form,fieldset,legend,header,
footer,nav,section,aside,dialog,figure,figcaption,hgroup,article,canvas{
	display: block;
}
ul{
	list-style: none;
}
a{
	text-decoration: none;
}
body{
	font-family:"Hiragino Sans GB","Hiragino SansGBW3",
	"Microsoft Yahei",STHeiti,SimSum,helvetica,arial,sans-s;
}
.ellipsis{
	white-space: nowrap;/*空白不换行*/
	overflow: hidden;/*溢出隐藏*/
	text-overflow: ellipsis;/*显示省略号*/
}
table{
	border-collapse:collapse ;
	border-spacing:0 ;
}
body{
  background-color: #f0f2f5;
  font-family: "Helvetica Neue";
  font-size: 14px;
  color: #444;
}
.app-header{
  background: #363636;
  color: #b2b2b2;
  height: 90px;
  line-height: 90px;
  width: 100%;
}
.app-header-inner{
  width: 1200px;
  margin: 0 auto;
}
.head-logo{
float: left;
}
.app-header-inner img{
  width: 50px;
  margin-top: 20px;
}
.header-nav{
  float: right;
}
.header-nav ul{
  overflow: hidden;
}
.header-nav li{
  cursor: pointer;
  float: left;
}
.nav-pile{
  padding: 0 10px;
}
.app-footer{
  text-align: center;
  height: 80px;
  width: 100%;
  line-height: 80px;
  background: #e3e4e8;
  clear: both;
  margin-top: 30px;
}
.container{
  width: 1200px;
  margin: 0 auto;
}
.hr{
  height: 1px;
  width: 100%;
  background: #ddd;
}
.button{
  background: #4fc08d;
  color: #fff;
  display: inline-block;
  padding: 10px 20px;
  cursor: pointer;
}
.button:hover{
  background: #4fc08d;
}
.g-form-line{
  padding: 15px 0;
}
.g-form-label{
  width: 100px;
  font-size: 16px;
  display: inline-block;
}
.g-form-input{
  display: inline-block;
}
.g-form-input input{
  height: 30px;
  width: 200px;
  line-height: 30px;
  vertical-align: middle;
  padding: 0 10px;
  border: 1px solid #ccc;
}
.g-form-btn{
  padding-left: 100px;
}
.g-form-error{
  color: red;
  padding-left: 15px;
}
</style>
