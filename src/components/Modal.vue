<template>
    <div class="modal_wrap" v-if="modalOpen === true">
        <div class="modal_box">
            <div class="modal_header">
                <h4 class="modal_title">
                    {{ products[number_modalClick].title }}
                </h4>
                <button
                    type="button"
                    class="close_btn"
                    @click="$emit('closeModal')"
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
                <div class="modal_input_box">
                    <input v-model="month" class="modal_input" type="number" />
                    개월
                </div>
                <p class="modal_price">
                    {{ month }} 개월 선택함:
                    {{ products[number_modalClick].price * month }}
                </p>
            </div>
        </div>
        <div class="modal_bg" @click="$emit('closeModal')"></div>
    </div>
</template>

<script>
export default {
    name: "Modal",
    data() {
        return {
            month: 1,
        };
    },
    watch: {
        month(number) {
            if (number >= 13) {
                alert(`12개월까지만 됩니다.`);
            }
        },
    },
    props: {
        products: Array,
        number_modalClick: Number,
        modalOpen: Boolean,
    },
};
</script>

<style>
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

.modal_box .modal_content .modal_input_box {
    display: flex;
    margin-top: 10px;
    white-space: nowrap;
    justify-content: center;
}

.modal_box .modal_content .modal_input {
    padding-left: 10px;
    margin-right: 10px;
    border: 1px solid #333;
}

.modal_box .modal_content .modal_price {
    margin-top: 10px;
}
</style>
