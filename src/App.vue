<template>
    <ul class="menu">
        <li v-for="item in menu" :key="item.id">
            <a href="#">{{ item }}</a>
        </li>
    </ul>

    <Discount />

    <Card
        @openModal="
            modalOpen = true;
            number_modalClick = $event;
        "
        :product="products[index]"
        v-for="(product, index) in products"
        :key="product.id"
    />

    <Modal
        :products="products"
        :number_modalClick="number_modalClick"
        :modalOpen="modalOpen"
    />
</template>

<script>
import oneroomData from "./assets/room.js";
import Discount from "./components/Discount.vue";
import Modal from "./components/Modal.vue";
import Card from "./components/Card.vue";

export default {
    name: "App",
    data() {
        return {
            number_modalClick: 0,
            menu: ["Home", "Products", "About"],
            products: oneroomData,
            modalOpen: false,
        };
    },
    methods: {
        increase(e, number) {
            this.products[number].reportNumber++;
        },
    },
    components: {
        Discount: Discount,
        Modal: Modal,
        Card: Card,
    },
};
</script>

<style>
* {
    margin: 0;
    padding: 0;
}

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

.menu {
    display: flex;
    background: #4f34eb;
    padding: 15px;
    border-radius: 5px;
    justify-content: center;
    list-style: none;
}

.menu a {
    color: #fff;
    padding: 10px;
    text-decoration: none;
}
</style>
