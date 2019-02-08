<template>
  <div id="app" class="container-fluid" v-bind:class="{'blocked':modalIsVisible}">
    <transition name="slide-fade">
      <modal-component :msg="modalStatus" v-if="modalIsVisible" @hideModalEvent="hideModal"/>
    </transition>
    <div class="row">
      <div class="col-12 pb-2 pl-5 pt-5"><h1>Contacts</h1></div>
    </div>
    
    <div class="row section">
      
        <div class="col-lg-6 px-5 pb-5">
          <h2 class="py-5"><span class="accent">GMS</span> Headquarters</h2>

            <div class="row">
              <div class="col-md-6">
                <p class="pb-3">
                  Global Message Services Ukraine LLC<br>
                  Bundesstrasse 5 | 3rd Floor<br>
                  6300 Zug<br>
                  Switzerland<br>
                </p>
                <a href="tel:+41415446200" class="tel-accent">+41 41 544 62 00</a>
              </div>
              <div class="col-md-6">
              Email<br>
              <a href="mailto:info@gms-worldwide.com" class="accent">info@gms-worldwide.com</a><br>
              Send message<br>
              <a href="mailto:info@gms-worldwide.com" class="accent">viber us</a><br>
              Send form<br>
              <a href="mailto:info@gms-worldwide.com" class="accent">contact us</a><br>
              </div>
            </div>
          
        </div>
        <div class="col-lg-6 px-5 pb-5">
          <h2 class="py-5">Technical support <span class="accent">24/7</span></h2>
          <div class="row">
            <div class="col-lg-8">
              <p class="pb-3">
              GMS understands that it can be hard
              to follow all new technologies.
              We regularly provide for all our clients
              educational trainings to make your operator`s business
              earn more and better though our best practices.
              </p>
              <a href="tel:+41415446200" class="tel-accent">+41 41 544 62 00</a>
            </div>
          </div>
        </div>

        </div>
      

    <div class="row section dark-bg">
        <div class="col-lg-6 pt-5 px-5">
            <h2>Our offices</h2>
            <div class="links py-5">
              <a href="#" @click.prevent="mapId = 131842" v-bind:class="{'active':mapId==131842}" class="mr-3 text-uppercase">Kiev</a>
              <a href="#" @click.prevent="mapId = 131843" v-bind:class="{'active':mapId==131843}" class="mr-3 text-uppercase">Barcelona</a>
              <a href="#" @click.prevent="mapId = 131844" v-bind:class="{'active':mapId==131844}" class="mr-3 text-uppercase">London</a>
              <a href="#" @click.prevent="mapId = 131845" v-bind:class="{'active':mapId==131845}" class="mr-3 text-uppercase">Kuev</a>
            </div>
            <h2 class="pb-3">Global Message Services Ukraine LLC</h2>
            <p class="small pb-5">
              Kuiv, Stepan Bandera, 33 <br>
              02066<br>
              Ukraine<br>
            </p>
        </div>
        <div class="col-lg-6 gmap">
          <map-component :id="mapId" />
        </div>
    </div>
    <div class="row section pattern pb-5 pt-5">
        <div class="col-lg-6 col-md-12 px-5">
          <h2 class="pb-5">Contact us</h2>
            <form-component @showModalEvent="showModal"/>
        </div>
        <div class="col-lg-6 col-md-12 px-5">
            Please tell us more about your request and give us info about your company and country
        </div>
        </div>
  </div>

</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import './scss/base.scss'

import mapComponent from './components/map.vue'
import formComponent from './components/form.vue'
import modalComponent from './components/modal.vue'

export default {
  name: 'app',
  data(){
    return {
      mapId:131842,
      modalIsVisible:false,
      modalStatus:false,
    }
  },
  methods:{
    showModal(e){
      this.modalStatus = e;
      this.modalIsVisible = true;
            
    },
    hideModal(){this.modalIsVisible = false},
  },
  components:{
    mapComponent,
    formComponent,
    modalComponent,
  }
}
</script>