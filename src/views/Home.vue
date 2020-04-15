<template>
<div class="home">
    <div class="search">
        <input type="text" v-model="query" @input="searchPedos" placeholder="Search persons by name" class="form-input">
        <button class="search__btn">
            <span data-feather="search"></span>
        </button>
    </div>
    <div class="">

        <h4 class="lead-text">
            <span id="typed"></span>
        </h4>

        <div id="typed-strings">
            <p> Hi 👋,^1000 <br /> Welcome!^1000 I would personally, and as a matter of opinion ^200 really like to call these folks potential pedophiles in the making.^500 However,^1000 I cannot for potential legal reasons😤.^1000 So instead, please find some really “funny” people found on Twitter^1000 (a public platform 🤷🏾‍♂️)^1000 making very “funny” comments at a 15year old minor. <br /> </p>
        </div>

        <div class="pedos">

            <pedo v-for="(pedo, id) in pedos" :key="id" :pedo="pedo" @show-image="showImage($event)"></pedo>
        </div>
    </div>

    <image-modal :show="showModal" :img="modalImg" @close="showModal = false"></image-modal>
</div>
</template>

<script>
require('../../public/feather');
import Pedo from '../components/Pedo';
import Tabletop from 'tabletop';

import ImageModal from '../components/ImageModal';
import Typed from 'typed.js';
export default {
    name: 'home',
    data() {
        return {
            pedos: [],
            results: [],
            query: "",
            showModal: false,
            modalImg: ""
        }
    },
    components: {
        Pedo,
        ImageModal
    },
    mounted() {
        feather.replace();

        console.log(Typed);

        var typed = new Typed('#typed', {
            stringsElement: '#typed-strings',
            typeSpeed: 50,
            showCursor: false
        });

        var publicSpreadsheetUrl = 'https://docs.google.com/spreadsheets/d/1_zCAl8I-5-I8f-SLUD3_Lg_b4ctliJUOFqorMNyk32k/edit?usp=sharing';

        Tabletop.init({
                key: publicSpreadsheetUrl,
                simpleSheet: true
            })
            .then(data => {
                this.pedos = data;
            });
    },
    computed: {
        list() {
            if (this.results.length == 0 || this.query == "") {
                return this.pedos;
            } else {
                return this.results;
            }
        }
    },
    methods: {
        searchPedos() {
            this.results = [...this.pedos].filter((val) => {
                // console.log(val);
                return val.name.toLowerCase().indexOf(this.query.toLowerCase());
            });

        },
        showImage(img) {
            this.modalImg = img;
            this.showModal = true;
        }
    }
}
</script>

<style>
.home {
    display: grid;
    grid-template-columns: minmax(500px, 80%);
    align-items: center;
    justify-content: center;
    margin: 100px 50px auto;
}

h2 {
    text-align: center;
}

.lead-text {
    text-align: center;
    max-width: 700px;
    margin: 0 auto;
    color: #777;
}

.search {
    width: 70%;
    margin: 30px auto;
    border: solid 1px rgba(0, 31, 63, 0.70);
    display: flex;
    align-items: center;
    height: 50px;
    border-radius: 10px;
    overflow: hidden;
}

.search .form-input {
    height: 100%;
    flex: 1;
    border: 0;
    outline: 0;
    padding: 5px 15px;
}

.search__btn {
    outline: none;
    border: none;
    background: transparent;
    padding: 8px 10px;
    margin-right: 8px;
    border-radius: 5px;
    cursor: pointer;
    transition: .5s all;
}

.search__btn .feather {
    width: 16px;
    height: 16px;
    color: #FF851B;
    transition: .5s all;
}

.search__btn:hover {
    background: #FF851B;
}

.search__btn:hover>.feather {
    color: #f2f2f2;
}

.pedos {
    margin: 30px auto;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    /* grid-auto-rows: 85%; */
    grid-column-gap: 50px;
    flex-direction: column;
    align-items: top;
}

a {
    color: #FF851B;
    text-decoration: none;
    transition: .5s all;
}

a:hover {
    text-decoration: underline;
}

@media screen and (max-width: 600px) {
    .home {
        grid-template-columns: 95%;
        margin: 100px 20px auto;
    }

    h1 {
        font-size: 22px;
    }

    .search {
        width: 90%;
        margin-bottom: 10px;
    }

    .pedos {
        width: 95%;
        grid-template-columns: 100%;
        grid-column-gap: 0;
    }

}
</style>
