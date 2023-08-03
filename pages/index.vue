<template>
  <div>
    <!-- {{ entry.data }} -->
    <table>
      <thead>
        <tr>
          <th>Nation</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in entry.data">
          <td>{{item.Nation}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData({ $axios }) {
    try {
      const response = await $axios.get('https://api.datausa.io/api/data?drilldowns=Nation&measures=Population')
      //console.log(response.data)
      return { entry: response.data }
    } catch (error) {
      //console.error('Error fetching data:', error.message)
      return { entry: null }
    }
  },
  data(){
    return{
      entry:[]
    }
  },
  mounted(){
    this.getData()
  },
  methods: {
    async getData() {
      
    }
  }
}
</script>
