<template>
  <div >

	<!-- Main Content -->
	<div class="container-fluid">
		<div class="row main-content bg-success text-center">
			<div class="col-md-4 text-center company__info">
			</div>
			<div class="col-md-8 col-xs-12 col-sm-12 login_form ">
				<div class="container-fluid">
					<div class="row ">
						<h2>Contact Us</h2>
					</div>
					<div class="row">
						<form @submit.prevent="send" class="form-group">
							<div class="row">
                              
								<input type="text" v-model="name" id="name"  name="name"  class="form__input" placeholder="Name">
							</div>
							<div class="row">
								<!-- <span class="fa fa-lock"></span> -->
								<input type="text" v-model="email" id="email" name="email" class="form__input" placeholder="E-mail">
							</div>
							<div class="row">
                                
								<textarea   v-model="message" class="form-control" id="message" name="message" placeholder="Your Message"></textarea>
								
							</div>
							<div class="row">
								<input type="submit" value="Submit" class="btn">
                                <label for="errorSignIn mx-3" class="form-text error-form">{{status}}</label>
							</div>
						</form>
					</div>
					<div class="row py-3">
						<p> You Don't have an account? <a href="#"> <router-link to="/signup"><span>Register Here</span></router-link> </a></p>
					</div>
				</div>
			</div>
		</div>
	</div>
	<!-- Footer -->
	<div class="container-fluid text-center footer">
		
	</div>

  </div>
</template>




<script>
     import axios from 'axios';

     export default {
          name: 'Contact',
          data() {
               return {
                    name   : '',
                    email  : '',
                    message: '',
                    status : ''
               }
          },
          methods: {
               send() {
                    const contact = {
                         name   : this.name,
                         email  : this.email,
                         message: this.message
                    }

                    axios.post('http://localhost:8000/admin/contact', contact)
                         .then(() => {
                             this.status = "message sended ...";
                             this.name = '';
                             this.email = '';
                             this.message = '';

                             })
                         .catch(err => console.log("contact error : ", err))
               }
          }
     }
</script>


<style scoped>
.main-content{
	width: 50%;
	border-radius: 20px;
	/* box-shadow: 0 5px 5px rgba(0,0,0,.4); */
	margin: 5em auto;
	display: flex;
}
.company__info{
	/* background-color: #9cc7c7; */
    background-image: url("https://images.pexels.com/photos/9902413/pexels-photo-9902413.jpeg");
    background-size: cover;
	border-top-left-radius: 20px;
	border-bottom-left-radius: 20px;
	display: flex;
	flex-direction: column;
	justify-content: center;
	/* color: #fff; */
}

@media screen and (max-width: 640px) {
	.main-content{width: 90%;}
	.company__info{
		display: none;
	}
	.login_form{
		border-top-left-radius:20px;
		border-bottom-left-radius:20px;
	}
}
@media screen and (min-width: 642px) and (max-width:800px){
	.main-content{width: 70%;}
}
/* .row > h2{
	color:#008080;
} */
.login_form{
	background-color: #fff;
	border-top-right-radius:20px;
	border-bottom-right-radius:20px;
	border-top:1px solid #ccc;
	border-right:1px solid #ccc;
}
form{
	padding: 0 2em;
    box-shadow: none !important ;
}
.form__input{
	width: 100%;
	border:0px solid transparent;
	border-radius: 0;
	border-bottom: 1px solid #aaa;
	padding: 1em .5em .5em;
	padding-left: 2em;
	outline:none;
	margin:1.5em auto;
	transition: all .5s ease;
}
.form__input:focus{
	/* border-bottom-color: #008080; */
	/* box-shadow: 0 0 5px rgba(0,80,80,.4);  */
	border-radius: 4px;
}
.btn{
	transition: all .5s ease;
	width: 70%;
	border-radius: 30px;
	color:#008080;
	font-weight: 600;
	background-color: #fff;
	border: 1px solid #008080;
	margin-top: 1.5em;
	margin-bottom: 1em;
}
.btn:hover, .btn:focus{
	background-color: #008080;
	color:#fff;
}
</style>