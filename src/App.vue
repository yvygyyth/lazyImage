 <template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Hello Vue 3.0 + Vite" />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  created(){
    this.getGoodList()
  },
  methods:{
    async getGoodList(){
      const {data:res} = await this.$http.get('/api/goods');
      console.log(res)
    }
  }
}
</script>
