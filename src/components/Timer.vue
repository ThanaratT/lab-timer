<template>
    <div>
        <span>countdown: </span>
        <span>{{ timeFormat }}</span>
    </div>
</template>
<script lang="ts">
import Vue from 'vue';
import { Component, Prop } from 'vue-property-decorator';
import Dayjs from 'dayjs';

@Component
export default class Timer extends Vue {
    @Prop({
      type: [Date, String, Number],
      default: null,
    })
    readonly startTime!: Date | string | number | null;

    timerInterval = null;

    remindTime = new Date(this.startTime).getTime();

    get timeFormat() {
      return Dayjs(this.remindTime).format('mm:ss');
    }

    countdown(): void {
      this.remindTime -= 1000;
    }

    mounted() {
      this.timerInterval = setInterval(this.countdown, 1000);
    }

    destroyed() {
      clearInterval(this.timerInterval);
    }
}
</script>
