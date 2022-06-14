<template>
    <div class="container">
      <h1 class="text-center">Test CRUD</h1>
      <div class="form-group row mt-2">
        <div class="col-3">
          <h4>Masukkan Email</h4>
          <input type="email" v-model="inputUser.email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" >
        </div>
        <div class="col-3">
          <h4>Masukkan Nama</h4>
          <input type="text" v-model="inputUser.name" class="form-control">
        </div>
        <div class="col-3">
          <h4>Masukkan Nomer Hp</h4>
          <input type="number" v-model="inputUser.phone" class="form-control">
        </div>
        <div class="col-3">
          <h4>Masukkan Username</h4>
          <input type="text" v-model="inputUser.username" class="form-control">
        </div>
      </div>
      <div class="row mt-2 mb-2 justify-content-center">
          <AddUserButton @callSubmitUser="submitUser()"/>
      </div>
      <table class="table">
        <thead>
          <tr>
            <th scope="col"></th>
            <th scope="col">Email</th>
            <th scope="col">Name</th>
            <th scope="col">Phone</th>
            <th scope="col">Username</th>
            <th scope="col"></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(bio, index) in listData" :key="bio.name">
            <th scope="row" >{{index + 1}}</th>
            <td>{{bio.email}}</td>
            <td>{{bio.name}}</td>
            <td>{{bio.phone}}</td>
            <td>{{bio.username}}</td>
            <td>
              <!-- <b-button class="btn btn-info" @click="updateUser(index)">Update User</b-button> -->
              <UpdateUserButton  @callUpdateUser="updateUser(index)"/>
              <!-- <button type="button" @click="deleteUser(index)" class="btn btn-danger">Delete</button> -->
              <DeleteUserButton @callDeleteUser="deleteUser(index)"/>
            </td>
          </tr>
        </tbody>
      </table>
      <b-modal ref="my-modal" hide-footer title="Update Data">
      <div class="d-block">
        <h4>Masukkan Email Baru</h4>
        <input type="email" v-model="updateEmail" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" >
      
        <h4>Masukkan Nama Baru</h4>
        <input type="text" v-model="updateName" class="form-control">
      
        <h4>Masukkan Nomer Hp Baru</h4>
        <input type="text" v-model="updatePhone" class="form-control">
      
        <h4>Masukkan Username Baru</h4>
        <input type="text" v-model="updateUsername" class="form-control">
      </div>
      <b-button class="mt-3" variant="outline-danger" block @click="updateSubmit()">Update User</b-button>
    </b-modal>
    </div>
</template>

<script>
import axios from 'axios';
import AddUserButton from '../components/AddUserButton.vue';
import UpdateUserButton from '~/components/UpdateUserButton.vue';
import DeleteUserButton from '../components/DeleteUserButton.vue';
export default {
  components: { AddUserButton, UpdateUserButton, DeleteUserButton },
  data(){
    return {
        listData:[],
        inputUser :{
          name:'',
          phone:'',
          username:'',
          email:''
        },
        updateName:'',
        updateEmail:'',
        updatePhone:'',
        updateUsername:'',
        updateIndex:0
    }
  },
  async created(){
    this.initUsers()
  },
  methods : {
    async initUsers(){
      const config = {
        headers: {
            Accept : "application/json"
        }
      };
      const res = await axios.get(`https://jsonplaceholder.typicode.com/users`, config);
      this.listData = res.data
      console.log(this.listData)
    },
    submitUser(){
      this.listData.push(this.inputUser)
      this.inputUser = []
    },
    deleteUser(index){
      this.listData.splice(index,1)
    },
    updateUser(index) {
      for ( let i = 0 ; i<this.listData.length;i++) {
        if(i == index) {
            this.updateName = this.listData[i].name
            this.updateUsername = this.listData[i].username
            this.updatePhone = this.listData[i].phone
            this.updateEmail = this.listData[i].email
        }
      }
      this.updateIndex = index
      this.$refs['my-modal'].show()
    },
    updateSubmit() {
      for ( let i = 0 ; i<this.listData.length;i++) {
        if(i == this.updateIndex) {
            this.listData[i].name = this.updateName
            this.listData[i].username = this.updateUsername
            this.listData[i].phone = this.updatePhone 
            this.listData[i].email = this.updateEmail
        }
      }
      this.$refs['my-modal'].hide()
    }
  }
};
</script>

<style>

</style>