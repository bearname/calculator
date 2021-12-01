<template>
  <!--  <img alt="Vue logo" src="./assets/logo.png">-->
  <!--  <HelloWorld msg="Welcome to Your Vue.js App"/>-->
  <Calculator/>
</template>

<script>

import Calculator from "./views/Calculator";

export default {
  name: 'App',
  components: {
    Calculator,
  }
}
</script>

<style>
@font-face {
  font-family: 'Lab Grotesque';
  src: url('assets/fonts/LabGrotesque-Regular.eot');
  src: local('Lab Grotesque Regular'), local('LabGrotesque-Regular'),
  url('assets/fonts/LabGrotesque-Regular.eot?#iefix') format('embedded-opentype'),
  url('assets/fonts/LabGrotesque-Regular.woff') format('woff'),
  url('assets/fonts/LabGrotesque-Regular.ttf') format('truetype');
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: 'Lab Grotesque';
  src: url('assets/fonts/LabGrotesque-Medium.eot');
  src: local('Lab Grotesque Medium'), local('LabGrotesque-Medium'),
  url('assets/fonts/LabGrotesque-Medium.eot?#iefix') format('embedded-opentype'),
  url('assets/fonts/LabGrotesque-Medium.woff') format('woff'),
  url('assets/fonts/LabGrotesque-Medium.ttf') format('truetype');
  font-weight: 500;
  font-style: normal;
}

* {
  padding: 0;
  margin: 0;
  text-align: left;

}

body {
  text-align: left;
}

button {
  background: none;
  outline: none;
  border: none;
  padding: 0;
}

.bg-primary {
  background: linear-gradient(255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;
  border-radius: 30px;
  padding: 30px;
}

#app {
  background: linear-gradient(255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;
  box-shadow: 0 0 24px rgba(234, 0, 41, 0.33);
  border-radius: 6px;

  font-family: 'Lab Grotesque', Arial, sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;
  text-align: center;

  /*color: #FFFFFF;*/
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

h3 {
  font-family: 'Lab Grotesque', Arial, sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 28px;
  line-height: 40px;
  color: #000000;
  text-align: left;
}

.caption {
  font-family: 'Lab Grotesque', Arial, sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  line-height: 24px;

  color: #000000;
}

p {
  /* Desktop/Body 14 */
  font-family: 'Lab Grotesque', Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 24px;

  color: #808080;
}

.flex {
  display: flex;
}

.spacer {
  margin-bottom: 24px;
}

.spacer-sm {
  margin-bottom: 8px;
}

.mr-10  {
  margin-right: 10px;
}

.pt-7 {
  padding-top: 7px;
}
</style>
