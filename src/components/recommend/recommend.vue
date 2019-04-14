<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
       
  </div>
</template>

<script>
import {getRecommend} from 'api/recommend'
import {ERR_OK} from 'api/config'
export default {
  name: 'recommend',
  data () {
    return {
      msg: '推荐'
    }
  },
  created(){
    this._getRecommend()
  },
  methods:{
    _getRecommend(){
      getRecommend().then((res) => {
        console.log(res)
          if (res.code === ERR_OK) {
            this.recommends = res.data.slider
          }
        })
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
