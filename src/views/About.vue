<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div>
      startTime {{ startTime }}
    </div>
    <Timer
      :start-time="startTime"
    />
  </div>
</template>
<script lang="ts">
import Vue from 'vue';
import { Component } from 'vue-property-decorator';

import Timer from '../components/Timer.vue';

@Component({
  components: {
    Timer,
  },
})
export default class About extends Vue {
  startTime = new Date('2021-04-17 23:55:00');
}
</script>
