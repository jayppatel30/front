<template>
	<div class = "page">
		<input type="text" v-model = "title"><br/>
		<h1>{{title}}</h1>
		<p v-if="showName">{{ user.firstName }}</p>
		<p v-else> {{user.lastName}}</p>
		<ul>
			<ul v-for=  "item in items">{{item.title}}</ul>
		</ul>
		<button v-on:click = "greet('Hello '+ user.firstName)">Say Greetings</button><br/>
		<input type = "text" v-on:keyup = "pressKey" v-on:keyup.enter = "enterHit">
		<hr />
		<lable> First Name: </lable><input type="text" v-model="user.firstName"><br/>
		<lable> First Name: </lable><input type="text" v-model="user.lastName"><br/>
		<h3>{{fullName}}</h3>
	</div>
</template>

<script>
	export default{
		name: 'page',
		props: {
			msg: {
				default: "Foobar"
			}
		},
		data() {
			return {
				title: 'hello world',
				user: {
					firstName: 'Jay',
					lastName: 'patel'
			 	},
			 	showName: true,
			 	items: [ 
			 		{title: 'Item one'},
			 		{title: 'Item two'},
			 		{title: 'Item three'}
			 	]
			}
		},
		methods: {
			greet : function(greeting){
				alert(greeting);
			},
			pressKey: function(e){
				console.log(e.target.value);
			},
			enterHit: function(){
				console.log('you hit enter');
			}
		},
		computed: {
			fullName: function(){
						return this.user.firstName+ ' ' + this.user.lastName;
			}
		} 
	}
</script>

<style scoped>
</style>