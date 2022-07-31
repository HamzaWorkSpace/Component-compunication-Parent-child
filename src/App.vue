<template>
  <section>
    <header>
      <h1>My Friends</h1>
    </header>

    <b-container class="bv-example-row">
     <button style="margin-left:45%" @click="toggleForm">{{ FormIsVisible ? 'Cancel' : 'AddFriend' }}</button>
        <br/>
        <br/>
      <b-row v-if="FormIsVisible">
        <div class="formsStyle">
        <b-col >

          <b-form inline>
                
                    <b-form-input
                      id="inline-form-input-name"
                      class="mb-2 mr-sm-2 mb-sm-0"
                      placeholder="Name"
                      v-model="fName"
                    />
                    <br/>
                    <b-form-input 
                    id="inline-form-input-username" 
                    placeholder="email"
                    v-model="fEmail"
                    />
<br/>
                     <b-form-input 
                    id="inline-form-input-username" 
                    placeholder="phone Number"
                    v-model="fPhone"
                    />
<br/>
                    <b-button @click="save" variant="primary">Save</b-button>
                    <br/>
          </b-form>

            
        </b-col>
     </div>
      </b-row>
    </b-container>

    <ul>
      <li v-for="friends in friendsList" :key="friends.name">
            <friend-contact
            :friend-name="friends.name"
            :friend-email="friends.email"
            :friend-phone="friends.fPhone"
          />
      </li>
    </ul>
  </section>
</template>

<script>

import FriendContact from './components/FriendContact.vue';

export default {
  components:{
    FriendContact
  },
  data() {
    return {
      FormIsVisible:false,

      fName:"",
      fEmail:"",
      fPhone:"",

      friendsList:[]
    };
  },
  methods:{
    toggleForm(){
     this.FormIsVisible = !this.FormIsVisible;
      this.fName="";
      this.fEmail="";
      this.fPhone="";
    },
    save(){

      this.friendsList.push({name:this.fName, email:this.fEmail, phone:this.fPhone});
      this.FormIsVisible = false;
      }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}
html {
  font-family: "Jost", sans-serif;
}
body {
  margin: 0;
}
header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
#app li {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}
#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}
#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

.formsStyle{
  width:50%;
  margin-left:25%;
}

</style>