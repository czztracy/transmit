<template>
	<div>
		<el-row class="container">
	        <homeheader :Number = "Id" @getNum="Son"></homeheader>
	    </el-row>
	    <el-container>
			<el-aside width="200px">
			  	<!--<el-button type="primary" @click="one" v-for="a in $router.options.routes[0].children">{{a.name}}</el-button>-->
			  	<el-button type="primary" @click="one"><i class="fa fa-ambulance">&nbsp;</i>第一个按钮</el-button>
				<el-button type="success" @click="two"><i class="fa fa-cab">&nbsp;</i>第二个按钮</el-button>
				<el-button type="info" @click="three"><i class="fa fa-plane">&nbsp;</i>第三个按钮</el-button>
				<el-button type="warning" @click="four"><i class="fa fa-subway">&nbsp;</i>第四个按钮</el-button>
				<el-button type="danger" @click="five"><i class="fa fa-rocket">&nbsp;</i>第五个按钮</el-button>
				<el-button type="primary" @click="logout" :loading="isLoginout"><i class="fa fa-rocket">&nbsp;</i>注销的按钮</el-button>
				<el-button type="primary"><i class="fa fa-rocket">&nbsp;</i>{{SonId}}</el-button>
			</el-aside>
		  	<el-main>
		  		<router-view></router-view>
		  	</el-main>
		</el-container>
	</div>
</template>

<script>
    import homeheader from './publicCom/header.vue';
    import '../api/api';
    export default {
        data() {
            return {
                isLoginout: false,
                Id: "父组件的Id： 1",
                SonId: '子组件'
            }
        },
        methods: {
        	one(){
        		this.$router.push({ path: 'one'});
        		this.$ajax.get('/data1.json'/*, params, { 
        			'headers':{'Content-Type':'application/json;charset=UTF-8'}
        		}*/).then( response => {
        			console.log(response)
        		}).catch( error => {
				    console.log(error);
				});
        	},
        	two(){
        		this.$router.push({ path: 'two'})
        	},
        	three(){
        		this.$router.push({ path: 'three'}) 
        	},
        	four(){
        		this.$router.push({ path: 'four'})
        	},
        	five(){
        		this.$router.push({ path: 'five'})
        	},
        	//退出登录
        	logout(){
		  		this.isLoginout = true;
		  		var _this = this;
		  		setTimeout( () => {
		  			sessionStorage.removeItem("user");
		  			console.log(sessionStorage.user)
		  			_this.isLoginout = false;
		  			_this.$router.push({ path: '/Login' });
		  			this.$store.dispatch('loginOut');
		  		}, 3000 );
		    },
		    //接收子组件传来的数据
		    Son(data) {
		    	//接收数据
		    	this.SonId = data;
		    	console.log(data)
		    }
        },
        mounted() {
        	
        },
        components: {
            homeheader
        }
    } 
</script>

<style scoped lang="scss">
button{
	margin-top: 20px; display: block;
}
.el-button {
    margin-left: 20px;
}
.el-main {
	text-align: center; padding: 0; 
}

</style>

