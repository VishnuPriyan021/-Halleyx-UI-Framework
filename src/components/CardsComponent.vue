<template>
<div class="card" :style="'width:' + this.width + 'px'" :class="{cardhover: this.hover, cardshadow: this.shadow, padding: this.padding, background: this.background, cardActive: this.active}">
    <div class="card-title" v-if="this.card_title == true">
        <header >
            <slot name="card-title">Card title</slot>
        </header>
    </div>
    <div class="card-body">
        <!-- {{this.card_body}} -->
        <main>
            <slot name="card-body">Card body</slot>
        </main>
    </div>
    <div class="card-footer" v-if="this.card_footer == true">
        <!-- {{this.card_footer}} -->
        <footer>
            <slot name="card-footer">Card footer</slot>
        </footer>
    </div>
</div>
</template>

<script>
export default {
  name: 'hlx-card',
  props: ['card_title', 'card_body', 'card_footer', 'width', 'hover', 'shadow', 'padding', 'background', 'active'],
  components: {
  },
  mounted () {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">

</style>
