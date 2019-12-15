
<template>
	<div class="tree-node">
		<div 
			class="tree-node__content"
			:style="{
				paddingLeft: data.level * indent + 'px'
			}"
			@click="handleNodeClick(data)">
			<span>{{ data.title }}</span>
		</div>
		<div class="tree-node__children">
			<tree-node
				v-show="data.expand"
				:data="node"
				v-for="(node, index) of data.children"
				v-on="$listeners"
				:key="index">
			</tree-node>
			<!-- 
				$listeners 属性是为了把组件的事件一层一层的发送到最外面的根节点,没有这个的画,事件将不能传输出去
			 -->
		</div>
	</div>
</template>

<script type="text/ecmascript">
	export default {
		name: 'tree-node',
		inject: {
			indent: {
				type: Number,
			}
		}, // 从高层组件里拿到缩进数据
		props: {
			data: {
				type: Object
			},
		},
		methods: {
			handleNodeClick(data){
				data.expand = !data.expand;
				this.$emit('node-click', data);
			}
		}
	}
</script>

<style lang="scss" scoped>
	.tree-node{
		&__content{
			&:hover {
				background: orange;
			}
		}
	}
</style>