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
                    <td>{{ item.Nation }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
  
<script>
export default {
    name: 'IndexPage',

    data() {
        return {
            entry: []
        }
    },
    mounted() {
        this.getData()
    },
    methods: {
        async getData() {
            try {
                const response = await this.$axios.get('https://api.datausa.io/api/data?drilldowns=Nation&measures=Population')
                this.entry = response.data
            } catch (error) {
                console.error("failed")
            }
        }
    }
}
</script>
  