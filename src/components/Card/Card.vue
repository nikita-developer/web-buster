<template>
    <div class="card">
        <div class="card__body">
            <div class="card__media">
                Вот такая картинка
            </div>
            <div class="card__title">{{card.name}}</div>
            <div class="card__description">{{card.description}}</div>
            <button class="card__button" @click="$emit('buy', card)">Заказать</button>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            card: {
                type: Object,
                default: {},
            },
        },
    }
</script>

<style lang="scss" scoped>
    @import 'styles/main.scss';
</style>