<template>
    <ul class="menu">
        <li v-for="item in menu" :key="item.id">
            <a href="#">{{ item }}</a>
        </li>
    </ul>

    <img alt="Vue logo" src="./assets/logo.png" />

    <div v-for="product in products" :key="product.id">
        <h4>{{ product.title }}</h4>
        <p>{{ product.price }} 만원</p>
    </div>
</template>

<script>
export default {
    name: "App",
    data() {
        return {
            menu: ["Home", "Products", "About"],
            products: [
                {
                    title: "역삼동 원룸",
                    price: 50,
                },
                {
                    title: "천호동 원룸",
                    price: 30,
                },
                {
                    title: "마포구 원룸",
                    price: 60,
                },
            ],
        };
    },
    components: {},
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
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
