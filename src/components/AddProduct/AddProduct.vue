<template>
    <form @submit.prevent="submit" class="add-product">
        <div class="add-product__background" @click="$emit('close')"></div>
        <div class="add-product__body">
            <h2 class="add-product__name">{{ card.name }}</h2>
            <p class="add-product__description">{{ card.description }}</p>
            <label class="add-product__label">
                <input
                    type="text"
                    v-model="email"
                    class="add-product__field"
                    :class="{'error': !success}"
                    placeholder="Введите свой email"
                    @input="validateEmail(email)"
                />
                <small v-if="!success">Не корректный email</small>
            </label>
            <button type="submit" class="add-product__button">Купить</button>
        </div>
    </form>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            success: true
        }
    },
    props: {
        card: {
            type: Object,
            default: {},
        },
    },
    methods: {
        submit() {
            if (this.validateEmail(this.email)) {
                fetch('mail.php', {
                    method: 'POST',
                    body: JSON.stringify({email: this.email, name: this.card.name, description: this.card.description}),
                    headers: { 'Content-Type': 'application/json;charset=utf-8' },
                })
                this.$emit('close')
            }
        },
        validateEmail(email) {
            if(/[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*@(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?/.test(String(email).toLowerCase())) {
                this.success = true
                return true
            }
            this.success = false
            return false
        }
    },
}
</script>

<style lang="scss" scoped>
@import 'styles/main.scss';
</style>
