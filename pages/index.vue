<template>
  <div class="container">
    <div class="header"></div>

    <div class="palette">
      <div class="palette-item" v-for="(color, index) in colors" :style="{background: color}">
<!--        <chrome-picker v-model="colors[index]"></chrome-picker>-->
        <p><i class="fas fa-sliders-h fa-2x fa-fw"></i></p>
        <br>
        <p><i class="fas fa-share-alt fa-2x fa-fw"></i></p>
        <br>
        <p><i @click="removeColor(color)" class="fas fa-trash fa-2x fa-fw"></i></p>
        <br>
        <input type="text" v-model="colors[index]">
      </div>
    </div>

    <div class="add-color" @click="addRandomColor">
      <p><i class="fas fa-plus"></i> add color</p>
    </div>

    <div class="footer">
      <footer>&copy; Copyright {{year}} Austin Barrett | made with <i class="fas fa-heart"></i>️ by <a
        href="//stripedpurple.io">Striped Purple Media</a></footer>
    </div>
  </div>
</template>

<script>
  import { Chrome } from 'vue-color';

  export default {
    data() {
      return {
        colors: ['#006BA6', '#0496FF', '#FFBC42', '#D81159', '#8F2D56']

      }
    },
    components: {
      'chrome-picker': Chrome
    },
    computed: {
      year() {
        return new Date().getFullYear()
      }
    },
    methods: {
      addRandomColor: function () {
        let letters = '0123456789ABCDEF';
        let color = '#';
        for (let i = 0; i < 6; i++) {
          color += letters[Math.floor(Math.random() * 16)];
        }
        this.colors.push(color);
      },
      removeColor: function (color) {
        this.colors.splice(this.colors.indexOf(color), 1)
      }
    }
  }
</script>

<style lang="sass">
  html,
  body,
  #__nuxt,
  #__layout,
  #__layout > div
    padding: 0
    margin: 0
    height: 100%
    min-height: 100%

    a
      text-decoration: none

    .fas.fa-heart
      color: #ab163f

    .container
      display: flex
      flex-direction: column
      height: 100%
      min-height: 100%
      text-align: center

      div
        display: flex
        flex-direction: column
        justify-content: center

      .palette
        background: #dadcd2
        display: flex
        flex-wrap: wrap
        flex: 1
        flex-direction: row

        .palette-item
          min-width: 20%
          flex-basis: 0
          flex-grow: 1
          flex-shrink: 1
          font-weight: bold
          color: rgba(255, 255, 255, 0.5)

          *:hover
            color: rgba(255, 255, 255, 0.75)


          input
            color: rgba(255, 255, 255, 0.5)
            background: transparent
            outline: none
            text-align: center
            font-size: 2rem
            font-weight: bold
            box-shadow: none
            border: 0

      .add-color
        background: #ab163f
        height: 3rem
        font-size: 1.5rem
        font-weight: bold
        color: #fff


      .header
        padding: 0 1.5rem
        height: 3rem !important
        background: #4947b4

      .footer
        padding: 0 1.5rem
        color: #cecece
        height: 3rem !important
        background: #252525

        a
          color: white
          font-weight: bold
</style>
