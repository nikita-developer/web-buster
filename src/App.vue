<template>
    <div class="page">
        <transition name="fade">
            <Preloader v-if="preloader"></Preloader>
        </transition>
        <h1 class="page__title">Каталог товаров</h1>
        <CardList
            class="page__card-list"
            :cards="cards"
            @buy="openModal"
        ></CardList>
        <transition name="fade">
            <AddProduct
                :card="card"
                v-if="showAddProduct"
                @close="showAddProduct = false"
            ></AddProduct>
        </transition>
        <Achievements></Achievements>
    </div>
</template>

<script>
import Achievements from './components/Achievements/Achievements.vue'
import AddProduct from './components/AddProduct/AddProduct.vue'
import CardList from './components/CardList/CardList.vue'
import Preloader from './components/Preloader/Preloader.vue'
export default {
    components: { CardList, AddProduct, Achievements, Preloader },
    data() {
        return {
            showAddProduct: false,
            card: null,
            preloader: true,
            cards: [
                {
                    id: 1,
                    name: 'Товар 1',
                    description:
                        'Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequuntur, ab!',
                },
                {
                    id: 2,
                    name: 'Товар 2',
                    description:
                        'Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequuntur, ab!',
                },
                {
                    id: 3,
                    name: 'Товар 3',
                    description:
                        'Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequuntur, ab!',
                },
                {
                    id: 4,
                    name: 'Товар 4',
                    description:
                        'Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequuntur, ab!',
                },
                {
                    id: 5,
                    name: 'Товар 5',
                    description:
                        'Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequuntur, ab!',
                },
                {
                    id: 6,
                    name: 'Товар 6',
                    description:
                        'Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequuntur, ab!',
                },
            ],
        }
    },
    methods: {
        openModal(val) {
            this.showAddProduct = true
            this.card = val
        },
    },
    mounted() {
        setTimeout(() => {
            this.preloader = false
        }, 1500)
    },
}
</script>

<style lang="scss">
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
body {
    font-family: sans-serif;
    font-size: 16px;
}

.page {
    padding-top: 30px;
    padding-bottom: 30px;

    &__add {
        margin-bottom: 60px;
        border: 0;
        border-radius: 20px;
        padding: 15px;
        color: #fff;
        font-weight: 700;
        background-color: #557de2;
        width: 100%;
        font-size: 14px;
        letter-spacing: 2px;
        text-transform: uppercase;
        cursor: pointer;

        &:hover {
            background-color: #4072f1;
        }
    }

    &__title {
        margin-bottom: 30px;
        text-align: center;
    }

    &__card-list {
        margin-bottom: 30px;
    }
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}
</style>
