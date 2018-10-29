<!--vue 第一次作业，新建人物信息并实现增删更改 -->
<template>
  <div id="app">

      <fieldset>
          <!--设置界面-->
          <legend>
              Create New Person
          </legend>
          <div class="form-group">
              <label>Name:</label>
              <input type="text" v-model="newPerson.name"/>
          </div>
          <div class="form-group">
              <label>Age:</label>
              <h1><input type="text" v-model="newPerson.age"/></h1>                   
              
          </div>
          <div class="form-group">
              <label class="la">Sex:</label>
              <select v-model="newPerson.sex">
                  <option value="Male">Male</option>
                  <option value="Female">Female</option>
              </select>
          </div>
          <div>
              <!--用v-if判断输入年龄大小，并给予一定提示-->
              <h1 v-if='newPerson.age >= 60'><font size='2'>Alter: old people</font></h1>
              <h1 v-else-if ='newPerson.age<=10'><font size='2'>Alter:children</font></h1>
              <h1 v-else><font size='2'>Aldult</font></h1>
          </div>
          <div class="form-group">
              <label></label>
              <center><button @click="createPerson">Create</button></center>
          </div>

      </fieldset>

      <table>
          <thead>
              <tr>
                  <th>Name</th>
                  <th>Age</th>
                  <th>Sex</th>
                  <th>Delete</th>
              </tr>
          </thead>
          <tbody>
              <!--显示已有人物信息-->
              <tr v-for="(person,index) in people" :key="person in people">
                  <td> <input  type = "text" v-model="person.name"></td>
                  <td> <input  type = "text" v-model="person.age"></td>
                  <td><input  type = "text" v-model="person.sex"></td>
                  <td :class="'text-center'"><button @click="deletePerson(index)">Delete</button></td>
              </tr>
          </tbody>
      </table>
  </div>

</template>

<script>
   //返回初始界面和数据
  export default {
    name: "app",
    data() {
      return {
        newPerson: {
          name: "",
          age: '',
          sex: "Male"
        },
        people: [
          {
            name: "Jack",
            age: 30,
            sex: "Male"
          },
          {
            name: "Bill",
            age: 26,
            sex: "Male"
          },
          {
            name: "Tracy",
            age: 22,
            sex: "Female"
          },
          {
            name: "Chris",
            age: 36,
            sex: "Male"
          }
        ]
      };
    },

  methods: {
    createPerson: function() {
      this.people.push(this.newPerson);
      // 创建新人物信息
      this.newPerson = { name: "", age: 0, sex: "Male" };
    },
    deletePerson: function(index) {
      // 删除人物信息
      this.people.splice(index, 1);
    }
    
  }
};
</script>