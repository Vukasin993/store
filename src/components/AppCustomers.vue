<template>
    <div>
        <h2>AppCustomers</h2>
        <form method="POST" @submit.prevent="DodajKupca">
            <input v-model="ime" type="text" placeholder="Unesi Ime">
            <input v-model="prezime" type="text" placeholder="Unesi Ime">
            <button>Dodaj Kupca</button>
        </form>
        <table>
      <tr> 
        <td>Ime</td>
        <td>Prezime</td>
        <td>Brisanje</td>
      </tr>
      <tr v-for="(customer,index) in customers" :key="index">
        <td>{{ customer.ime }}</td>
        <td>{{ customer.prezime }}</td>
        <td><button @click="izbrisatiKupca(index)">Remove</button></td>
      </tr>
    </table>
    </div>
</template>

<script>
export default {
    data () {
          return {
  
          customers: [
              { ime: 'Pera', prezime: 'Peric'},
              { ime: 'Mika', prezime: 'Mikic'},
              { ime: 'Djuro', prezime: 'Djuric'}
          ],
        }
    },
    ime: '',
    prezime: '',

    methods: {
        izbrisatiKupca(index) {
            this.customers.splice(index,1);
        },
        DodajKupca() {
            const newCustomer = {
                ime: this.ime,
                prezime: this.prezime
            }

            this.customers.push(newCustomer)
            this.ime = '',
            this.prezime =''
        }
    }
}
</script>

<style lang="stylus">

</style>