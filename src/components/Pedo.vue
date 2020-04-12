<template>
    <div class="card">
        <div class="card__body">
            <div class="card__body__img">
                <img src="https://i.pinimg.com/170x/b2/a4/cd/b2a4cd996937f47862bf0aca69442c2e.jpg" alt="">
            </div>
            <div class="card__body__content">
                <h4 class="name">John Does</h4>
            </div>

            <div class="card__body__border">
                <div class="card__body__border__item"></div>
                <div class="card__body__border__item"></div>
                <div class="card__body__border__item"></div>
                <div class="card__body__border__item"></div>
                <div class="card__body__border__item"></div>
                <div class="card__body__border__item"></div>
                <div class="card__body__border__item"></div>
                <div class="card__body__border__item"></div>
                <div class="card__body__border__item"></div>
                <div class="card__body__border__item"></div>
                <div class="card__body__border__item"></div>
                <div class="card__body__border__item"></div>
            </div>
        </div>

        <div class="card__image">
            <img src="https://via.placeholder.com/900x500.png" alt="">
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style>
.card {
    position: relative;
    width: 100%;
    height: 18vw;
    margin-bottom: 20px;
    /* margin-bottom: calc(20% + 20px); */ 
    /* transition: margin-bottom 0s; */
}

@media screen and (max-width: 1349px) {
    .card{
        height: 27vw;
    }
}

@media screen and (max-width: 912px) {
    .card{
        height: 55vw;
    }
}

@media screen and (max-width: 640px) {
    .card{
        height: 60vw;
    }
}

@media screen and (max-width: 600px) {
    .card{
        height: 67vw;
    }
}

.card__image {
    position: absolute;
    top: 50px;
    width: calc(100% - (50px + 30px + 15px));
    padding-top: calc(.66 * (100% - 95px));
    right: 15px;
    border-radius: 10px;
    overflow: hidden;
}

.card__image img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.card__body {
    background: #fff;
    width: 100%;
    box-shadow: 0 3px 15px rgba(0, 0, 0, 0.15);
    border-radius: 5px;
    position: relative;
    overflow: hidden;
    cursor: pointer;
    padding: 15px;
    padding-bottom: 40%;
    display: flex;
    transition: 1s all ease;
}

.card__body__img {
    height: 50px;
    width: 50px;
    border-radius: 5px;
    overflow: hidden;
}

.card__body__img img {
    height: 100%;
    width: 100%;
    object-fit: cover;
}

.card__body__content {
    margin-left: 15px;
}

.card__body__content .name {
    font-size: 18px;
    margin-top: 5px;
}

.card__body:hover{
    padding-bottom: 56%;
}

.card__body:hover>.card__body__border {
    display: flex;
    animation: 3s slide ease-in-out;
    opacity: 1;
}

.card__body::after {
    content: "";
    height: 5px;
    position: absolute;
    width: 120%;
    bottom: 0;
    left: -10%;
    background-color: #FF851B;
}

.card__body__border {
    height: 5px;
    position: absolute;
    left: -50%;
    bottom: 0;
    width: 200%;
    display: flex;
    align-items: center;
    justify-content: space-evenly;
    z-index: 100;
    display: none;
    opacity: 0;
}

.card__body__border__item {
    width: 4.1%;
    height: 100%;
    background-color: #234AAB;
}

@keyframes slide {
    0% {
        left: -20px;
        opacity: 0;
    }

    20% {
        opacity: 1;
    }

    100% {
        left: -50%;
    }
}
</style>
