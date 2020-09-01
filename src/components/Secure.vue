<template>
  <div>
    <h1>This page is protected by auth</h1>
    <!-- <div>{{ cities }}</div> -->
    <ul>
      <li v-for="city in cities" :key="city.id">
        <!-- id : {{ city.id }} -->
        <!-- name :  -->{{ city.name }}
        <!-- address : {{ city.address }}
        phone : {{ city.phone }}
        email : {{ city.email }}
        email_for_callback : {{ city.email_for_callback }}
        active : {{ city.active }}
        sequence : {{ city.sequence }}
        created_at : {{ city.created_at }}
        updated_at : {{ city.updated_at }}
        deleted_at : {{ city.deleted_at }}
        letter : {{ city.letter }} -->
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Secure',
  data () {
    return {
      cities: null
    }
  },
  mounted () {
    var newHttp = this.$http.create()
    delete newHttp.defaults.headers.common['Authorization']

    newHttp
      .get('https://a3990709.fvds.ru/content')
      .then(response => (this.cities = response.data.data.cities))
      .catch(error => console.log(error))
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul{
  list-style-type: none
}
</style>
