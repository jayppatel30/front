<template>
	<div class = "user">
		<h1> User </h1>
		<form v-on:submit = "addUser">
			<label>First Name:&emsp;&emsp;&nbsp;&nbsp; </label><input type="text" pattern= "[a-zA-Z][a-zA-Z]{1,}" v-model="newUser.firstname" placeholder="Enter First Name"> 
			<br/>
			<label>Last Name:&emsp;&emsp;&emsp;</label><input type="text" v-model="newUser.lastname" pattern= "[a-zA-Z][a-zA-Z]{1,}" placeholder="Enter Last Name"> 
			<br/>
			<label>Email:&emsp;&emsp;&emsp;&emsp;&emsp;</label><input type="email" v-model="newUser.email" placeholder="Enter Email"><br/> 
			<label>Date Of Birth: &emsp;</label><input type="date" v-model="newUser.dob" placeholder="Enter dob" value="mm-dd-yyyy"><br/>

			<div class = "styled-select slate">
			<label>State: &emsp;&emsp;&emsp;&emsp;&nbsp;</label> 
			<select name = "state" v-model = "newUser.state" placeholder = "Enter State">
				<option value=""></option>
                <option value="AL">Alabama</option>
                <option value="AK">Alaska</option>
                <option value="AZ">Arizona</option>
                <option value="AR">Arkansas</option>
                <option value="CA">California</option>
                <option value="CO">Colorado</option>
                <option value="CT">Connecticut</option>
                <option value="DE">Delaware</option>
                <option value="DC">District Of Columbia</option>
                <option value="FL">Florida</option>
                <option value="GA">Georgia</option>
                <option value="HI">Hawaii</option>
                <option value="ID">Idaho</option>
                <option value="IL">Illinois</option>
                <option value="IN">Indiana</option>
                <option value="IA">Iowa</option>
                <option value="KS">Kansas</option>
                <option value="KY">Kentucky</option>
                <option value="LA">Louisiana</option>
                <option value="ME">Maine</option>
                <option value="MD">Maryland</option>
                <option value="MA">Massachusetts</option>
                <option value="MI">Michigan</option>
                <option value="MN">Minnesota</option>
                <option value="MS">Mississippi</option>
                <option value="MO">Missouri</option>
                <option value="MT">Montana</option>
                <option value="NE">Nebraska</option>
                <option value="NV">Nevada</option>
                <option value="NH">New Hampshire</option>
                <option value="NJ">New Jersey</option>
                <option value="NM">New Mexico</option>
                <option value="NY">New York</option>
                <option value="NC">North Carolina</option>
                <option value="ND">North Dakota</option>
                <option value="OH">Ohio</option>
                <option value="OK">Oklahoma</option>
                <option value="OR">Oregon</option>
                <option value="PA">Pennsylvania</option>
                <option value="RI">Rhode Island</option>
                <option value="SC">South Carolina</option>
                <option value="SD">South Dakota</option>
                <option value="TN">Tennessee</option>
                <option value="TX">Texas</option>
                <option value="UT">Utah</option>
                <option value="VT">Vermont</option>
                <option value="VA">Virginia</option>
                <option value="WA">Washington</option>
                <option value="WV">West Virginia</option>
                <option value="WI">Wisconsin</option>
                <option value="WY">Wyoming</option>
              </select>   
              </div>    
			<br/> 
				<label>Sex: &emsp;&emsp;&emsp;&emsp;&emsp;</label><input type="radio" v-model="newUser.sex" value="male" />Male&emsp;
				<input type="radio" v-model="newUser.sex" value= "female"/> female &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<br />
			<input type="submit">
		</form>
		<table style="width:100%">
  		<tr>
		    <th>Firstname</th>
		    <th>Lastname</th> 
		    <th>email</th>
		    <th>Date of birth</th>
		    <th>Sex</th>
		    <th>State</th>
  		</tr>
		<tr v-for= "user in user">
			<td>{{user.firstname}}</td>
			<td>{{user.lastname}}</td> 
			<td>{{user.email}}</td>
			<td>{{user.dob}}</td>
			<td>{{user.sex}}</td>
			<td>{{user.state}}</td>
			<button v-on:click = "deleteUser(user)">x</button>
  		</tr>
		</table>
	</div>
</template>

<script>
	export default{
		name: 'user',
		data() {
			return {
				newUser: {},
				user: []
			}
		},
		methods: {
			addUser: function(e){
				if(this.newUser.firstname == (null)){
					alert("first name is empty")
					e.preventDefault();
				}
				else if (this.newUser.lastname == (null)){
					alert("last name is empty")
					e.preventDefault();
				}
				else if (this.newUser.email == (null)){
				 	alert("Email is empty")
				 	e.preventDefault();
				}
				else if (this.newUser.dob == (null)){
					alert("add your birthdate")
					e.preventDefault()
				}
				else if (this.newUser.state == (null)){
					alert("State is not selected")
					e.preventDefault()
				}
				else if (!(this.newUser.sex == ('male') || this.newUser.sex == ('female'))) {
					alert("select your sex")
					e.preventDefault()
				}
				else {
					this.user.push({
						firstname: this.newUser.firstname,
						lastname: this.newUser.lastname,
						email: this.newUser.email,
						dob: this.newUser.dob,
						state: this.newUser.state,
						sex: this.newUser.sex,
						contacted: false
					})
					e.preventDefault();
				}
			},
			deleteUser: function(user){
				this.user.splice(this.user.indexOf(user),1)
			},
			clearField: function() {
			   if(document.getElementById) {
			      document.chatform.reset();
			      e.preventDefault();
			   }
			}
		}
	}
</script>

<style scoped>
div {
    border-radius: 5px;
    background-color: #f2f2f2;
    padding: 20px;
}
input[type=text], select {
    width: 50%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}

input[type=text]:focus {
    background-color: lightblue;
}

input[type=email], select {
    width: 50%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}

input[type=email]:focus {
    background-color: lightblue;
}

input[type=Date], select {
    width: 50%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}

input[type=date]:focus {
    background-color: lightblue;
}

.styled-select select {
	height: 40px;
 	width: 52%;
    padding: 12px 20px;
    margin: -5px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}

input[type=submit] {
    width: 20%;
    background-color: #4CAF50;
    color: white;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

input[type=submit]:hover {
    background-color: #45a049;
}


table {
    font-family: arial, sans-serif;
    border-collapse: collapse;
    width: 100%;
}

td, th {
    border: 1px solid #dddddd;
    text-align: left;
    padding: 8px;
}

tr:nth-child(even) {
    background-color: #dddddd;
}
</style>