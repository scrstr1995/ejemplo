<template>
<LegoHeader/>
 <div id="exampleModal">
      <!-- Button trigger modal-->
      <!-- Modal-->
      <transition @enter="startTransitionModal" @after-enter="endTransitionModal" @before-leave="endTransitionModal" @after-leave="startTransitionModal">
        <div class="modal fade" v-if="showModal" ref="modal">
          <div class="modal-dialog" role="document">
            <div class="modal-content">
              <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
                <button class="close" type="button" @click="showModal = !showModal"><span aria-hidden="true">×</span></button>
              </div>
              <div class="modal-body">...</div>
              <div class="modal-footer">
                <button class="btn btn-secondary" @click="showModal = !showModal">Close</button>
                <button class="btn btn-primary" type="button">Save changes</button>
              </div>
            </div>
          </div>
        </div>
      </transition>
      <div class="modal-backdrop fade d-none" ref="backdrop"></div>
    </div>
  <div class="row">
<div  class="card col-lg-2" v-for="goku in gokus" :key="goku.id" >
    <img class="card-img-top" :src="goku.imageUrl"  alt="Card image cap" :width="200" :height="200">
  <div class="card-body">
    <h5 class="card-title">{{goku.name}}</h5>
    <p class="card-text">Origen: {{goku.originplanet}}</p>
   <button class="btn btn-primary m-5" type="button" @click="showModal = !showModal">Launch demo modal</button>
      
  </div>
</div>
  </div>
</template>

<script>
import LegoHeader from './LegoHeader'
import axios from 'axios';
export default {
  name: 'LegoMain',
    data () {
    return {
      gokus: null,
        showModal: false,
    }

  },
  methods: {
        startTransitionModal() {
          this.$refs.backdrop.classList.toggle("d-block");
          this.$refs.modal.classList.toggle("d-block");
        },
        endTransitionModal() {
          this.$refs.backdrop.classList.toggle("show");
          this.$refs.modal.classList.toggle("show");
        }
      },
  
  props: {

    }
    ,components:{
      LegoHeader
    },
     beforeCreate() {
    console.log('At this point, events and lifecycle have been initialized.')
  },
      mounted () {
    axios
      .get('https://dragon-ball-super-api.herokuapp.com/api/characters')
      .then(response => (this.gokus = response.data))
  }

}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
