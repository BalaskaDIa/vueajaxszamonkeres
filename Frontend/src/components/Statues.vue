<template>
  <div>
      <h1>Szobrok</h1>
      <table>
        <thead>
            <tr>
                <th>Személy</th>
                <th>Magasság</th>
                <th>Ár</th>
                <th>Műveletek</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="statue in statues" v-bind:key="statue.id">
                <td>{{ statue.person }}</td>
                <td>{{ statue.height }}</td>
                <td>{{ statue.price }}</td>
                <td>
                    <button>Szerkesztés</button>
                </td>
                <td>
                    <button @click="torles(statue.id)">Törlés</button>
                </td>
            </tr>
            <tr>
                    <td>
                    <input type="text">
                </td>
                    <td>
                    <input type="number">
                </td>
                    <td>
                    <input type="number">
                </td>
                    <td>
                    <button>Mentés</button>
                </td>
                    <td>
                    <button>Mégse</button>
                </td>
                </tr>
        </tbody>
      </table> 
  </div>
</template>

<script>
export default {
  name: 'Statues',
  data()  {
      return {
          statue: {
              id: null,
              person: '',
              height: '',
              price: '',
          },
        statues: []
      }
  },
  methods: {
      async loadData() {
          let Response = await fetch('http://127.0.0.1:8000/api/statues');
          let data = await Response.json();
          this.statues = data;
  },
  
  async torles(id) {
      let Response = await fetch(`http://127.0.0.1:8000/api/statues/${id}`, {
          method: 'DELETE'
      });
      console.log(Response);
      await this.loadData();
  },

  frissites() {
      this.statue = {
          id: null,
          person: '',
          height: '',
          price: ''
      };
    }
  },

    mounted() {
    this.loadData();
  }
}
</script> 