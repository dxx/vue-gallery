<template>
	<div :class="className" @click="handleClick">
		<span>{{index + 1}}</span>
		<img :src="inverseSrc" class="inverse-icon"/>
	</div>
</template>

<script>
import inverseSrc from "../assets/inverse.svg"

export default {
	name: "imageController",
	props: ["index", "position"],
	data: function(){
		return {
			inverseSrc
		};
	},
	computed: {
		className: function(){
			let position = this.position;

			let className = "controller-unit" + (position.center === true ? " current" : "");
			if(position.inverse === true) className += " inverse";
			return className;
		}
	},
	methods: {
		handleClick: function(e){
			e.preventDefault();
			e.stopPropagation();

			if(this.position.center !== true){
				this.$emit("center", this.index)
			}else{
				this.$emit("inverse", this.index);
			}
		}
	}
}
</script>

<style scoped>
/*
 * 控制单元组件相关样式
 */
.controller-unit{
	position: relative;
	display: inline-block;
	width: 22px;
	height: 22px;
	line-height: 22px;
	margin-right: 15px;
	border-radius: 22px;
	background-color: #555555;
	color: #FFFFFF;
	vertical-align: middle;
	font-size: 14px;
	cursor: pointer;
	-webkit-transition: background-color .6s ease-in-out, transform .6s ease-in-out;
	transition: background-color .6s ease-in-out, transform .6s ease-in-out;
}
.controller-unit:hover{
	background-color: #121212;
}
.controller-unit.current{
	background-color: #121212;
}
.inverse-icon{
	display: none;
	position: absolute;
	top: 3px;
	left: 3px;
	width: 16px;
	height: 16px;
}
.controller-unit.current span{
	display: none;
}
.controller-unit.current .inverse-icon{
	display: block;
}
.controller-unit.inverse{
	-webkit-transform: rotateY(180deg);
	transform: rotateY(180deg);
}
/**
 * 去掉处理移动端点击出现背景效果
 */
@media screen and (max-width: 768px){ 
	.controller-unit{
		cursor: default;
	}
}
</style>