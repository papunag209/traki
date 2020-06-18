<template>
  <div class="whole-inputs">
    <h1>This is an tables page</h1>
    <table>
        <thead>
            <tr>
                <th>
                    Id
                </th>
                <th>
                    Name
                </th>
                <th>
                    Address
                </th>
                <th>
                    Birth Date
                </th>
                <th>
                    Contact
                </th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(item, index) in rows"
                :key="'table-row-'+index"
            >
                <td>
                    {{item.id}}
                </td>
                <td>
                    {{item.name}}
                </td>
                <td>
                    {{item.address}}
                </td>
                <td>
                    {{item.birthDate}}
                </td>
                <td>
                    {{item.contacts}}
                </td>
            </tr>
        </tbody>
    </table>
  <div class="inputs">
    <form @submit.prevent="handleSubmit">
        <p> 
            <span>
                <label for="id-input">Id:</label>
                <input 
                    id="id-input" type="number"
                    v-model="rowInput.id"    
                >
            </span>
            <span>
                <label for="name-input">Name:</label>
                <input
                    id="name-input" type="text"
                    v-model="rowInput.name"
                >
            </span>
            <span>
                <label for="address-input">Address:</label>
                <input
                    id="address-input" type="text"
                    v-model="rowInput.address"
                >
            </span>
            <span>
                <label for="birth-date-input">Birth Date:</label>
                <input id="birth-date-input" type="date"
                    v-model="rowInput.birthDate"
                >
            </span>
        </p>
        <div>
            <label>Contact info</label>
            <div @click.prevent="addContactField"><button>add more info</button></div>
            <ul>
                <li v-for="(contact, index) in rowInput.contacts"
                    :key="'contact-'+index"
                >
                    <span>
                        <label for="contact-input">Contact info:</label>
                        <input id="contact-input" type="text"
                            v-model="rowInput.contacts[index]"
                        >
                    </span>
                </li>
            </ul>
        </div>
        <span>
            <button type="submit">Submit</button>
        </span>
    </form>
  </div>
  </div>
</template>
<script>
import Vue from 'vue'

export default Vue.extend({
    name: 'TablesDemo',
    data: function () {
        return {
            rowInput: {
                id: '',
                name: '',
                address: '',
                birthDate: '',
                contacts: [],
            },
            rows: [],
        }
    },
    methods: {
        handleSubmit () {
            console.log('submitting')
            this.rows.push(this.rowInput)
            this.rowInput = {
                id: '',
                name: '',
                address: '',
                birthDate: '',
                contacts: [],
            }
        },
        addContactField () {
            this.rowInput.contacts.push('')
        }

    }
})
</script>

<style scoped>
*{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

.inputs{
    background-color:rgb(255, 207, 145) ;
    width: auto;
    height: 200px;
    overflow: auto;
    margin: auto;
    box-shadow: 2px 2px rgba(0, 0, 0, 0.274);
}

input{
    height: 30px;
    border: none;
    outline: none;
    border-bottom: solid gray;
    background: transparent;
}

p{
    padding: 5px;
}

label{
    padding: 5px;
}
button{
    color:#fff;
	background-color:#757575;
	outline: none;
    border: 0;
	padding:8px;
    margin-top: 5px;
	text-transform:uppercase;
	border-radius:2px;
	cursor:pointer;
	position:relative;
    box-shadow: 1px 1px black;
}
</style>