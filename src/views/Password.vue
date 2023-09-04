<template>
  <v-container>
    <v-row justify="center">
      <v-col align-self="center" cols="8">
        <GeneratorCard/>
      </v-col>
    </v-row>
            <v-row justify="center">
                <v-col align-self="center" cols="8">
                    <span class="disclaimer">Algorithm for password generation from <a href src="http://tinyurl.com/jsgenpassword">this tutorial</a></span>
                </v-col>
            </v-row>
  </v-container>
</template>

<script setup>
  import GeneratorCard from '@/components/GeneratorCard.vue'
</script>

<style>

.disclaimer {
  font-size: 10px;
  font-weight: 40;
  color: black;
  float: right;
}

.disclaimer a {
  text-decoration: none;
}

</style>
