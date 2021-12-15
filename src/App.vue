<template>
    <ul class="menu">
        <li v-for="item in menu" :key="item.id">
            <a href="#">{{ item }}</a>
        </li>
    </ul>

    <div v-for="(product, index) in products" :key="product.id">
        <img
            :src="require(`@/assets/${product.image}`)"
            class="room-img"
            alt="룸 이미지"
        />
        <h4
            @click="
                modalOpen = true;
                number_modalClick = index;
            "
            class="product_title"
        >
            {{ product.title }}
        </h4>
        <p class="product_content">{{ product.content }}</p>
        <p class="product_price">{{ product.price }} 만원</p>
        <button type="button" class="report_btn" @click="increase(e, index)">
            허위매물신고
        </button>
        <span class="report_number">신고수 : {{ product.reportNumber }}</span>
    </div>

    <div class="modal_wrap" v-if="modalOpen === true">
        <div class="modal_box">
            <div class="modal_header">
                <h4 class="modal_title">
                    {{ products[number_modalClick].title }}
                </h4>
                <button
                    type="button"
                    class="close_btn"
                    @click="modalOpen = false"
                >
                    닫기
                </button>
            </div>
            <div class="modal_content">
                <img
                    :src="
                        require(`@/assets/${products[number_modalClick].image}`)
                    "
                    class="modal_cont_img"
                    alt="룸 이미지"
                />
                <p class="modal_cont_info">
                    {{ products[number_modalClick].content }}
                </p>
            </div>
        </div>
        <div class="modal_bg" @click="modalOpen = false"></div>
    </div>
</template>

<script>
import oneroomData from "./assets/room.js";

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
    components: {},
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

.product_title {
    font-size: 20px;
    margin-bottom: 10px;
}

.product_content {
    margin-bottom: 10px;
}

.product_price {
    margin-bottom: 10px;
}

.report_btn {
    background: #6750ec;
    color: #fff;
    border: 0;
    padding: 5px;
    border-radius: 6px;
}

.report_number {
    margin-left: 10px;
}

.room-img {
    width: 100%;
    margin: 40px 0 30px;
}

.modal_wrap {
    overflow: hidden;
}

.modal_box {
    position: fixed;
    top: 50%;
    left: 50%;
    padding: 20px;
    transform: translate(-50%, -50%);
    background: #fff;
    border-radius: 14px;
    z-index: 1;
}

.modal_box .modal_header {
    position: relative;
    display: flex;
    padding-right: 50px;
    padding-bottom: 10px;
    margin-bottom: 10px;
    border-bottom: 1px solid #333;
}

.modal_box .modal_title {
    word-break: break-word;
    text-align: left;
    font-size: 20px;
}

.modal_box .modal_header .close_btn {
    position: absolute;
    top: -10px;
    right: 0;
    width: 30px;
    height: 30px;
    background: transparent;
    border: 0;
    text-indent: -9999px;
}

.modal_box .modal_header .close_btn:before,
.modal_box .modal_header .close_btn:after {
    content: "";
    position: absolute;
    left: 15px;
    height: 30px;
    width: 2px;
    background-color: #000;
}

.modal_box .modal_header .close_btn:before {
    transform: rotate(45deg);
}

.modal_box .modal_header .close_btn:after {
    transform: rotate(-45deg);
}

.modal_box .modal_content .modal_cont_img {
    width: 100%;
}

.modal_box .modal_content .modal_cont_info {
    font-size: 15px;
    text-align: left;
}

.modal_wrap .modal_bg {
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.3);
}
</style>
