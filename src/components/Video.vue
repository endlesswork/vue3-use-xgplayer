
<template>
	<div class="video-module">
		<div>
			<h1>mp4播放</h1>
			<h2></h2>
		</div>
		<div class="content">
			<div style="display: flex; flex-direction: column;"
				v-for="(item,index) in videoList" :key="index">
				<div>{{item.id}}</div>
				<div>
					<div :id="item.id"></div>
				</div>
				<button @click="handleRemove(item,index)">移除</button>
			</div>
		</div>
	</div>
	
	
</template>
<script setup>
	import { ref,nextTick } from 'vue';
	import Player from 'xgplayer';
	const videoList = ref([]);
	add();
	function add(){
		let that = this;
		let list = [];
		let item0 = {
			'url':'http://clips.vorwaerts-gmbh.de/big_buck_bunny.mp4',
			'id': 'item0'
		}
		let item1 = {
			'url':'//sf1-cdn-tos.huoshanstatic.com/obj/media-fe/xgplayer_doc_video/mp4/xgplayer-demo-360p.mp4',
			'id': 'item1'
		}
		let item2 = {
			'url':'//sf1-cdn-tos.huoshanstatic.com/obj/media-fe/xgplayer_doc_video/mp4/xgplayer-demo-360p.mp4',
			'id': 'item2'
		}
		list.push(item0);
		list.push(item1);
		list.push(item2);
		videoList.value = list;
		nextTick(()=>{
			let player0 = new Player({
			  id: item0.id,
			  volume: 0,
			  url: item0.url,
			  width: 200
			});
			item0.player = player0;
			player0.on('destroy',()=>{
				console.log('player0 destroy');
				videoList.value.splice(0, 1);
			}); 
			let player1 = new Player({
			  id: item1.id,
			  volume: 0,
			  url: item1.url,
			  width: 200
			});
			item1.player = player1;
			player1.on('destroy',()=>{
				console.log('player1 destroy');
				videoList.value.splice(0, 1);
			}); 
			let player2 = new Player({
			  id: item2.id,
			  volume: 0,
			  url: item2.url,
			  width: 200
			});
			item2.player = player2;
			player2.on('destroy',()=>{
				console.log('player2 destroy');
				videoList.value.splice(0, 1);
			}); 
		});
		
	}
	function handleDestroy(item){
		console.log(1111);
		
	}
	function handleRemove(item, index){
		item.player.destroy();
		/* console.log("remove:", index);
		this.videoList.splice(index, 1);
		for(let i=0; i<this.videoList.length; i++){
			console.log("remove item id: %s,url: %s", this.videoList[i].id,this.videoList[i].url );
		} */
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
	flex-direction: column;
}
.video-module .content{
	display: flex;
}
</style>
