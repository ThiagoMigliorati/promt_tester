<template>
  <div>
    <page-title :heading=heading :subheading=subheading :icon=icon></page-title>

    <div class="content">
      
    </div>
  </div>
</template>

<script>

  import PageTitle from "../../Layout/Components/PageTitle.vue";

  export default {
    components: {
      PageTitle,

    },
    data: () => ({
      heading: 'Blank Page',
      subheading: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
      icon: 'pe-7s-voicemail icon-gradient bg-arielle-smile',



    }),


  }
</script>
