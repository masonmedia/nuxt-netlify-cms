<template>
  <div class="">
    <nav-component></nav-component>
    <b-jumbotron
      class="
        d-flex
        flex-column
        justify-content-center
        align-items-start
        bg-light
        min-vh-100
        mb-0
        px-5
      "
    >
      <h1 class="display-2 font-weight-bold">Welcome</h1>
      <p class="col-sm-8 h4 font-weight-light">
        Laborum tempor duis sunt dolor velit officia dolor sint ad aute culpa
        voluptate pariatur velit. Esse adipisicing officia laborum deserunt
        nisi. Culpa ullamco culpa laborum ex do magna veniam dolore exercitation
        sint. Velit ea exercitation ex ea ullamco do velit ullamco ipsum aute
        tempor.
      </p>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  head() {
    return {
      script: [
        { src: "https://identity.netlify.com/v1/netlify-identity-widget.js" },
      ],
    };
  },
};
</script>