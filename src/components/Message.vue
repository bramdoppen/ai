


<template>
    <div class="message">
      <span>Hello {{name}}</span>
      <span>How can I help?</span>
    </div>
</template>

<script>
import { gsap } from "gsap";

export default {
  name: 'Message',
  props: ["userName"],
  mounted() {
    var tl = gsap.timeline();
    tl.fromTo(".message > *:first-child", {y: 30, opacity: 0}, {y: 0, opacity: 1, duration: 1.4}, "+=0.8");
    tl.to(".message > *:first-child", {y: -20, opacity: 0, duration: 1}, ">");
    tl.fromTo(".message > *:last-child", {y: 30, opacity: 0}, {y: 0, opacity: 1, duration: 1.4}, ">");
  },
  computed: {
      name() {
          return this.userName;
      }
  }
}
</script>

<style>

.message {
  font-size: 40px;
  display: flex;
  position: relative;
  width: 100%;
  text-align: center;
  justify-content: center;
}
.message > * {
  opacity: 0;
  display: inline-flex;
  position: absolute;
  top: 0;
}
</style>
