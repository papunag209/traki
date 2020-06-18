<template>
  <div>
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
    <form @submit.prevent="handleSubmit">
        <p>

            <span>
                <label for="id-input">Id</label>
                <input 
                    id="id-input" type="number"
                    v-model="rowInput.id"    
                >
            </span>
            <span>
                <label for="name-input">Name</label>
                <input
                    id="name-input" type="text"
                    v-model="rowInput.name"
                >
            </span>
            <span>
                <label for="address-input">Address</label>
                <input
                    id="address-input" type="text"
                    v-model="rowInput.address"
                >
            </span>
            <span>
                <label for="birth-date-input">Birth Date</label>
                <input id="birth-date-input" type="date"
                    v-model="rowInput.birthDate"
                >
            </span>
        </p>
        <div>
            <label>Contact info</label>
            <div @click.prevent="addContactField">Add Contact Line + </div>
            <ul>
                <li v-for="(contact, index) in rowInput.contacts"
                    :key="'contact-'+index"
                >
                    <span>
                        <label for="contact-input">Contact info</label>
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

</style>