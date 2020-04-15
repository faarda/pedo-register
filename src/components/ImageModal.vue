<template>
<div class="modal-container" :class="show ? 'modal-container--show' : ''" id="modal">
    <div class="image-modal">
        <span class="image-modal__close" @click="closeModal"><span data-feather="x"></span></span>
        <div class="image-modal__body">
            <div class="image-modal__image">
                <img :src="img" alt="">
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: "image-modal",
    props: {
        show: {
            default: false,
            type: Boolean
        },
        img: {
            required: true,
            type: String
        }
    },
    mounted() {
        feather.replace();

    },
    methods: {
        closeModal(){
            this.$emit('close');
        }
    }
}
</script>

<style>
.modal-container {
    position: fixed;
    width: 100vw;
    height: 100vh;
    z-index: 50000;
    top: 0;
    left: 0;
    background: rgba(0, 31, 63, 0.7);
    display: none;
    transition: 1s cubic-bezier(0.075, 0.82, 0.165, 1) all;
}

.modal-container--show{
    display: block !important;
}

.modal-container .image-modal {
    background: #fff;
    margin: 5vh auto;
    width: 80vw;
    height: 90vh;
    border-radius: 15px;
    padding: 3rem;
    position: relative;
}

@media screen and (max-width: 450px) {
    .modal-container .image-modal {
        width: 90vw;
        padding: 1.5rem;
    }
}

.modal-container .image-modal__close {
    position: absolute;
    display: inline-block;
    right: 15px;
    top: 15px;
    cursor: pointer;
}

.modal-container .image-modal__body {
    display: flex;
    height: 100%;
    width: 100%;
}

@media screen and (max-width: 450px) {
    .modal-container .image-modal__body {
        flex-direction: column;
    }
}

.modal-container .image-modal__image {
    flex: 1;
    width: 100%;
    height: 100%;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
}

@media screen and (min-width: 450px) {
    .modal-container .image-modal__image {
        padding: 0 2rem;
    }
}

.modal-container .image-modal__image img {
    max-height: 100%;
    max-width: 100%;
    border-radius: 15px;
    position: relative;
    /* border: solid 1px #ccc; */
}


@media screen and (max-width: 450px) {
    .modal-container .image-modal__meta {
        width: 100%;
        height: 28%;
        padding: 1.5rem 0;
        border: 0;
    }
}

</style>
