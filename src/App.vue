<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <p>
    <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#subscribeApp">
      Subscribe
    </button>
  </p>
  
  <div class="modal fade" id="subscribeApp" tabindex="-1" aria-labelledby="subscribeAppLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="image">
        </div>
        <div class="modal-body">
          <p class="p-align">
            <span class="percent">
              10% off
            </span>
          </p>
          <p class="p-align">
            <span class="percent-to-text">
              your first order
            </span>
          </p>
          <hr class="hr-line">
          <span class="adv">
            Subscrive to recieve 10% off promocode plus exclusive offers and deals
          </span>
            <div v-if="subscribeSuccess" class="alert alert-success">
              You have successfully subscribed to the newsletter
            </div>
            <div v-if="subscribeFail" class="alert alert-danger">
              You have already subscribed to the newsletter
            </div>
            <label for="userEmail">
              Email-adress
            </label>
            <input type="email" v-model="userEmail" class="form-control" id="userEmail">
            <button type="button" class="subscribe-button" @click="toSubscribe">
              Subscribe!
            </button>
            <div class="form-check">
              <input type="checkbox" class="form-check-input" id="privacy-agree">
              <label class="form-check-label" for="privacy-agree">
                  I'm agree with privacy policy
              </label>
            </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'subscribeApp',
  
  data() {
    return {
      userEmail: '',
      subscribeSuccess: false,
      subscribeFail: false
    }
  },
  
  methods: {
    toSubscribe() {
      let getIssetEmail = localStorage.getItem('emailToSubscribe');
      if (getIssetEmail == this.userEmail) {
        this.subscribeFail = true;
        this.subscribeSuccess = false;
      } else {
        localStorage.setItem('emailToSubscribe', this.userEmail);
        this.subscribeSuccess = true;
        this.subscribeFail = false;
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.modal-body {
  text-align: left;
  position: absolute;
}
.image {
  position: absolute;
  width: 1400px;
  height: 700px;
  top: -350px;
  background: url('assets/image.png');
  transform: rotate(30deg);
}
.percent {
  color: #2F3639;
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 700;
  font-size: 104px;
  line-height: 100%;
}
.percent-to-text {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 700;
  font-size: 24px;
  line-height: 100%;
  color: #828688;
}
.adv {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 120%;
  display: flex;
  align-items: center;
  color: #595E61;
}
.hr-line {
  height: 2px;
  width: 67px;
  background-color: #C24DFE;
}
.subscribe-button {
  background: #C24DFE;
  border-radius: 35px;
  color: white;
  border: none;
}
.modal-dialog {
 overflow: hidden;
}
.modal-header {
  z-index: 1;
}
</style>
