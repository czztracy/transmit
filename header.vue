<template>
	<Menu mode="horizontal" theme="primary">
        <div class="layout-logo"> 
        	<span class="Name" @click="Goto">{{name}}</span>
        </div>
    </Menu>
</template>

<script>
	export default {
		props:['Number'],
		data() {
			return {
				name: "VUE",
				SId: "子组件的数据"
			}
		},
		methods: {
			Goto(){
				this.$router.push({
					path: '/Home2'
				});
			}
		},
		mounted(){
			//发送数据
			this.$emit("getNum", this.SId);		
			console.log(this.$router.options);
			console.log(this.Number);
		}
	}
</script>

<style lang="scss">

</style> 