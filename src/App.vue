<template>
  <Scene>
    <Camera type="arcRotate"></Camera>
    <Torus :options="{diameter:5, thickness:0.1}" :position="[0, 0, 0]">
      <Animation property="rotation.x" :duration="5">
        <Key frame="0%" :value="0"></Key>
        <Key frame="100%" :value="Math.PI * 2"></Key>
      </Animation>
      <Animation
        property="rotation.y"
        :duration="10"
        :end="Math.PI"
      ></Animation>
      <Animation
        property="rotation.z"
        :duration="10"
        :end="Math.PI"
      ></Animation>
      <Material diffuse="#FFF"></Material>
    </Torus>
    <Torus :options="{diameter:5, thickness:0.1}" :position="[0, 0, 0]">
      <Animation property="rotation.x" :duration="5">
        <Key frame="0%" :value="0"></Key>
        <Key frame="100%" :value="Math.PI * 2"></Key>
      </Animation>
      <Animation
        property="rotation.y"
        :duration="5"
        :end="Math.PI * 2"
      ></Animation>
      <Animation
        property="rotation.z"
        :duration="5"
        :end="Math.PI * 2"
      ></Animation>
      <Material diffuse="#FF69B4"></Material>
    </Torus>
    <Entity>
      <Animation
        property="rotation.x"
        :duration="5"
        :end="Math.PI * 2"
      ></Animation>
      <!-- Standard Light component props-->
      <PointLight diffuse="#F0F" :position="[0, 0, 4]"></PointLight>
    </Entity>
    <Entity>
      <Animation
        property="rotation.y"
        :duration="5"
        :end="Math.PI * 2"
      ></Animation>
      <!-- Property components-->
      <PointLight>
        <property name="diffuse" color="#8A2BE2"></property>
        <property name="position" :vector="[0, 0, 4]"></property>
      </PointLight>
    </Entity>
    <Entity>
      <Animation
        property="rotation.z"
        :duration="5"
        :end="Math.PI * 2"
      ></Animation>
      <!-- Properties prop object on Entity component (set multiple values!)-->
      <!-- $color() helper function-->
      <PointLight
        :properties="{
          diffuse: $color('#8A2BE2'),
          specular: $color({ r: 1, g: 0, b: 0 }),
        }"
      >
        <!-- Mix-and-match!-->
        <property name="position" :vector="[0, 4, 0]"></property>
      </PointLight>
    </Entity>
  </Scene>
</template>
<script>
export default {
  data() {
    return {
      box: null,
      sphere: null,
      time: performance.now(),
      frames: 0,
    };
  },

  computed: {
    scale() {
      let a = 2 + Math.cos(this.time * 0.001);
      let b = 2 + Math.sin(this.time * 0.001);
      return {
        box: [a, b, 1],
        sphere: [b, a, 1],
      };
    },
  },

  methods: {},
};
</script>

<style></style>
