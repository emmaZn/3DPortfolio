<template>
  <Scene v-model="scene">
    <Camera type="arcRotate"></Camera>
    <Torus
      v-model="circle"
      :options="{ diameter: 6, thickness: 0.1 , tessellation:60 }"
      :position="[0, 0, 0]"
    >
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
    <Torus :options="{ diameter: 6, thickness: 0.1, tessellation:60 }" :position="[0, 0, 0]">
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
      <PointLight diffuse="#FF69B4" :position="[0, 0, 4]"></PointLight>
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
// import * as BABYLON from "babylonjs";
export default {
  data: function () {
    return {
      circle:null,
      scene:null,
    };
  },
  // mounted() {
  //   var hl = new BABYLON.HighlightLayer("hl1", this.scene);
  //   hl.addMesh(this.circle, BABYLON.Color3.Green());
  // },
  methods: {},
};
</script>

<style></style>
