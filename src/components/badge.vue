/* eslint-disable vue/multi-word-component-names */
/* eslint-disable vue/multi-word-component-names */
<template>
  <div class="badge" :id="address">
    <img :src=image width="300" />
    <h2 class="title">{{ address }}</h2>
  </div>
</template>
    
<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Badge',
  props: {
    address: String,
    image: String
  }
}
</script>
    
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.badge {
  display: flex;
  flex-direction: column;
  text-align: center;
  justify-content: center;
  align-items: center;
  color: #212121;
}

.badge>img:hover {
  cursor: pointer;
  transition: 350ms;
  transform: scale(1.2);
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}

.badge>img {
  height: 120px;
  width: 120px;
  transition: 350ms;
  border-radius: 100%;


}

@media only screen and (max-width: 800px) {

  .title {
    font-size: 15px;
    max-width: 90px;
  }

  .badge {
    display: flex;
    text-align: center;
    justify-content: center;
    align-items: center;
  }

  .badge>img {
    height: 60px;
    width: 60px;

    border-radius: 100%;

  }
}


.title:hover {
  cursor: pointer;
}

.badge-img {
  border-radius: 50%;
  transition: box-shadow .3s;
  border: 4px #f6e767 solid;
}

.badge-img:hover {
  box-shadow: 0 0 11px rgba(33, 33, 33, .6);
}

h3 {
  position: relative;
  text-decoration: none;
}

h3:before {
  content: "";
  position: absolute;
  width: 100%;
  height: 2px;
  bottom: -5px;
  left: 0;
  background-color: #000;
  visibility: hidden;
  -webkit-transform: scaleX(0);
  transform: scaleX(0);
  -webkit-transition: all 0.3s ease-in-out 0s;
  transition: all 0.3s ease-in-out 0s;
}

.badge:hover>h3:before {
  visibility: visible;
  -webkit-transform: scaleX(1);
  transform: scaleX(1);
}
</style>