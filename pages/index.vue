<template>
  <div class="container">
    <div class="header"></div>
    <div class="palette">
      <div class="palette-item" v-for="color in colors" :style="{background: color}">
        {{color}}
      </div>
    </div>
    <div class="add-color" @click="getRandomColor">
      <p><i class="fas fa-plus"></i> add color</p>
    </div>
    <div class="footer">
      <footer>&copy; Copyright {{year}} Austin Barrett | made with <i class="fas fa-heart"></i>️ by <a href="//stripedpurple.io">Striped Purple Media</a></footer>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      colors: ['#006BA6','#0496FF','#FFBC42','#D81159','#8F2D56']

    }
  },
  computed: {
    year() {
      return new Date().getFullYear()
    }
  },
  methods:{
    getRandomColor: function () {
    let letters = '0123456789ABCDEF';
    let color = '#';
    for (let i = 0; i < 6; i++) {
      color += letters[Math.floor(Math.random() * 16)];
    }
      this.colors.push(color);
    }
  }
}
</script>

<style lang="sass">
  html,
  body
    padding: 0
    margin: 0
    height: 100%

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
