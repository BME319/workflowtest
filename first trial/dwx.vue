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
                    <th>Delete</th>
                    <th>Modify</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(person, index) in people">
                    <td v-if="pos!=index">{{ person.name }}</td>
                    <td v-else><input type="text" v-model="person.name"/></td>
                    <td v-if="pos!=index">{{ person.age }}</td>
                    <td v-else><input type="number" v-model="person.age"/></td>
                    <td v-if="pos!=index">{{ person.sex }}</td>
                    <td v-else><input type="text" v-model="person.sex"/></td>
                    <td :class="'text-center'"><button @click="deletePerson(index)">Delete</button></td>
                    <td :class="'text-center'" v-if="pos!=index"><button @click="modifyPerson(index)">Modify</button></td>
                    <td :class="'text-center'" v-else><button @click="savePerson(index)">Save</button></td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: 'Homework',
    data () {
        return {
            newPerson: {
                name: '',
                age: 0,
                sex: 'Male'
            },
            pos: -1,
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
    methods: {
        createPerson: function () {
            this.people.push(this.newPerson);
            // 添加完newPerson对象后，重置newPerson对象
            this.newPerson = {name: '', age: 0, sex: 'Male'}
        },
        deletePerson: function(index){
            // 删一个数组元素
            this.people.splice(index,1);
        },
        modifyPerson: function(index){
            // 转化页面
            this.pos = index;
        },
        savePerson: function(index){
            // 改回原来
            this.pos = -1;
        }
    }
}
</script>