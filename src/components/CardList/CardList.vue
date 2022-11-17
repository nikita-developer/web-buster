<template>
    <div class="card-list">
        <Card
            v-for="card in cards"
            :key="card.id"
            :card="card"
            class="card-list__item"
            @buy="$emit('buy', card)"
        ></Card>
    </div>
</template>

<script>
import Card from '../Card/Card.vue'
export default {
    components: { Card },
    props: {
        cards: {
            type: Array,
            default: [],
        },
    },
}
</script>

<style lang="scss" scoped>
@import 'styles/main.scss';
</style>
