<template>
  <div>
      <h1>Szobrok</h1>
      <table class="table table-sm table-striped table-dark">
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
                    <button id="btn_szurke" @click="szerkesztes(statue.id)">Szerkesztés</button>
                    <button id="btn_narancs" @click="torles(statue.id)">Törlés</button>
                </td>
            </tr>
            <tr>
                    <td>
                    <input type="text" v-model="statue.person">
                </td>
                    <td>
                    <input type="number" v-model="statue.height">
                </td>
                    <td>
                    <input type="number" v-model="statue.price">
                </td>
                    <td>
                    <button v-if="ujSzobor" @click="mentes()">Mentés</button>
                    <button id="btn_szurke" v-if="!ujSzobor" @click="szerkesztesMentese()">Mentés</button>
                    <button id="btn_narancs" @click="frissites()">Mégse</button>
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

  async mentes() {
      await fetch('http://127.0.0.1:8000/api/statues', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
            'Accept': 'application/json'
          },
          body: JSON.stringify(this.statue)
      });
      await this.loadData();
      this.frissites();
  },

  async szerkesztes(id) {
      let Response = await fetch(`http://127.0.0.1:8000/api/statues/${id}`);
      let data = await Response.json();
      this.statue = {...data};
      this.ujSzobor = false;
  },

  async szerkesztesMentese() {
      await fetch(`http://127.0.0.1:8000/api/statues/${this.statue.id}`, {
                method: 'PATCH',
                headers: {
                    'Content-Type': 'application/json',
                    'Accept': 'application/json'
                },
                body: JSON.stringify(this.statue) 
            });
            this.loadData();
            this.frissites();
            this.ujSzobor = true;
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