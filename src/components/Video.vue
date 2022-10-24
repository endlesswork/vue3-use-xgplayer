
<template>
	<div class="video-module">
		<div>
			<h1>mp4播放</h1>
		</div>
		<div class="content">
			<div style="display: flex; flex-direction: column;"
				v-for="(item,index) in videoList" :key="index">
				<div>
					<div :id="item.id">{{item.id}}</div>
				</div>
				<button>移除</button>
			</div>
		</div>
	</div>
	
	
</template>
<script setup>
	import { ref } from 'vue';
	import Player from 'xgplayer';
	const videoList = ref([]);
	add();
	function add(){
		let list = [];
		let item0 = {
			'url':'',
			'id': 'item0'
		}
		let item1 = {
			'url':'',
			'id': 'item1'
		}
		let item2 = {
			'url':'',
			'id': 'item2'
		}
		list.push(item0);
		list.push(item1);
		list.push(item2);
		videoList.value = list;
	}
</script>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
.video-module{
	display: flex;
}
</style>
