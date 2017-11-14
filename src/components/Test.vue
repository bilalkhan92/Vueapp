<template>
<div class="test">
<input type="text" v-model="title"><br/>
	<h1>{{title}}</h1>
	<p v-if="showname">{{user.firstName}} {{user.lastName}}</p>
	<p v-else="showname">person</p>
	<ul>
		<li v-for="item in items">{{item.title}}</li>
	</ul>
	<button v-on:click="greet('Hello World')">Say Hello</button>
	<input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit">
	<hr />
	<label>First Name:</label><input type="text" v-model="user.firstName"><br/>
	<label>Last Name:</label><input type="text" v-model="user.lastName">
	<h3>{{fullname}}</h3>
	<h2>{{msg}}</h2>
</div>
</template>

<script>
	export default {
		name: 'test',
		props: {
			msg: {
				type: String,
				default:'Foobar'
			}
		},
		data() {
			return{
				title: 'Default Interpolations',
				user: {
					firstName: 'Bilal',
					lastName: 'Khan'
				},
				showname: true,
				items: [
					{title: 'Item One'},
					{title: 'Item Two'},
					{title: 'Item Three'}
				]
			}
		},
		methods: {
			greet: function(greeting){
				alert(greeting);
			},
			pressKey: function(e){
				console.log(e.target.value);
			},
			enterHit: function(){
				console.log('You hit enter');
			},
		},
		computed: {
				fullname: function(){
					return this.user.firstName+' '+this.user.lastName;
				}
			}

	}
</script>
<style scoped>
	
</style>