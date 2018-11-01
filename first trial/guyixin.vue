<template>
 <div id="app">

        <fieldset>
            <legend>
                    Create New Person
            </legend>
            <div class="form-group">
                    <label>Name:</label>
                    <input type="text" v-model="newPerson.name"/>
            </div>
            <div class="form-group">
                    <label>Age:</label>
                    <input type="text" v-model="newPerson.age"/>
            </div>
            <div class="form-group">
                <label>Sex:</label>
                <select v-model="newPerson.sex">
                    <option value="Male">Male</option>
                    <option value="Female">Female</option>
                </select>
            </div>
            <div class="form-group">
                <label></label>
                <button @click="createPerson">Create</button>
            </div>
        </fieldset>
        <table>
            <thead>
                <tr>
                    <th>Name</th>
                    <th>Age</th>
                    <th>Sex</th>
                    <th>Operation</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="person in people"
                     :key="person.index"> 
                    <td v-if="opt !=index">{{ person.name }}</td>
                    <td v-else><input type="text" v-model="person.name"></td>
                    <td v-if="opt !=index">{{ person.age }}</td>
                    <td v-else><input type="number" v-model="person.age"></td>
                    <td v-if="opt !=index">{{ person.sex }}</td>
                    <td v-else><input type="text" v-model="person.sex"></td>
                    <td :class="'text-center'"><button @click="deletePerson(index)">Delete</button></td>
                    <td :class="'text-center'" v-if="opt !=index"><button @click="editPerson(index)">Edit</button></td>
                    <td :class="'text-center'" v-else><button @click="save(index)">save</button></td>
                   
                    
                </tr>
            </tbody>
        </table>
        

        </div>

</template>


<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
        opt:-1, //初始位置不选中
       newPerson: {
                    name: '',
                    age: 0,
                    sex: 'Male'
                },
                
                people: [{
                    name: 'Jack',
                    age: 30,
                    sex: 'Male'
                }, {
                    name: 'Bill',
                    age: 26,
                    sex: 'Male'
                }, {
                    name: 'Tracy',
                    age: 22,
                    sex: 'Female'
                }, {
                    name: 'Chris',
                    age: 36,
                    sex: 'Male'
                }],
                


    }

  },
   methods:{
                createPerson: function(){
                    this.people.push(this.newPerson);
                    // 添加完newPerson对象后，重置newPerson对象
                    this.newPerson = {name: '', age: 0, sex: 'Male'}
                },
                deletePerson: function(index){
                    // 删一个数组元素
                    this.people.splice(index,1);
                },
                editPerson:function(index){
                     this.opt=index;//修改数组元素
                     
                    

                },
                save:function(index){
                    this.opt=-1;//重置指针
                }

                
               


            },
    


}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

