<template>
    <div>
        <img
            :src="require(`@/assets/${product.image}`)"
            class="room-img"
            alt="룸 이미지"
        />
        <h4 class="product_title" @click="$emit('openModal', product.id)">
            {{ product.title }}
        </h4>
        <p class="product_content">{{ product.content }}</p>
        <p class="product_price">{{ product.price }} 만원</p>
        <button type="button" class="report_btn" @click="increase(e, index)">
            허위매물신고
        </button>
        <span class="report_number">신고수 : {{ product.reportNumber }}</span>
    </div>
</template>

<script>
export default {
    name: "Card",
    data() {
        return {};
    },
    props: {
        product: Object,
    },
    methods: {},
};
</script>

<style>
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
</style>
