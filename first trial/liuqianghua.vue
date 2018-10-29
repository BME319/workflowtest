<template>
  <div id="app">
      <!--增加新信息-->
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
        <!--创建表格，显示所有信息，并有修改，保存和删除功能-->
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
                <tr v-for="(person,index) in people">
                    <td>
                        <input type="text" v-model="person.name" v-if="edi===index">
                        <span v-else>{{person.name}}</span>
                    </td>
                    <td>
                        <input type="text" v-model="person.age" v-if="edi===index">
                        <span v-else>{{person.age}}</span>
                    </td>
                    <td>
                        <input type="text" v-model="person.sex" v-if="edi===index">
                        <span v-else>{{person.sex}}</span>
                    </td>
                    <td>
                        <!--点击不同按钮实现不同功能-->
                        <button @click="modifyData(index)">Modify</button>
                        <button @click="saveData(index)">Save</button>
                        <button @click="deletePerson(index)">Delete</button>
                    </td>
                </tr>
            </tbody>       
        </table>
  </div>
</template>

<script>
export default {
  name: 'mywork',
  data () {
      return{
          edi:'',
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
                }]
      }
  },
  methods:{
      createPerson: function(){
          this.people.push(this.newPerson);
          this.newPerson = {name: '', age: 0, sex: 'Male'}
      },
      deletePerson: function(index){
          this.people.splice(index,1);
      },
      modifyData: function(index){
          this.edi=index;
      },
      saveData:function(index){
          this.edi=!index;
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div{
    vertical-align:middle;
}
th,td{
    text-align:center;
    height:50px;
    vertical-align:center;
}

table{
    border-collapse:collapse;
    text-align:center;
}
table,th, td{
    border: 1px solid black;
}
th{
    background-color: #42b983;
}

fieldset,table {
    width:50%;
    margin:0 auto;
}
div,th{
    height:50px;
}


</style>
