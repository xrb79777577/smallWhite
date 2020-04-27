<template>
  <div class="home">
    <div v-for="(v,i) in arr" :key="i">
      <label>
        输入框
        <input type="text" :placeholder="v.name" />
      </label>
    </div>
    <button @click="add()">新增一行</button>
    <button @click="deleteThree(2)">删除第三行</button>
    <button @click="deleteAll()">删除全部</button>
  </div>
</template>

<script>

export default {
 data(){
   return{
     arr:[
       {name:''},
       {name:''},
       {name:'本条删除'},
       {name:''}
     ]
   }
 },
 created(){
   let arrs=JSON.parse(sessionStorage.getItem('arr'))
   if(arrs != null){
     this.arr=arrs
   }
 },
 methods:{
   deleteThree(n){
     this.arr.splice(n,1)
     this.Sessions()
   },
   deleteAll(){
     debugger
     this.arr=[]
     this.Sessions()
   },
   add(){
     let addName={name:''}
     this.arr.push(addName)
     this.Sessions()
   },
   Sessions(){
     sessionStorage.setItem('arr',JSON.stringify(this.arr))
   }
 }
}
</script>
