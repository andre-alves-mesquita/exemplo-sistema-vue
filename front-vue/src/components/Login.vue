<template>
    <div class="columns divFull zeroMP">
        <div class="column fundoImagem"></div>
        <div class="column is-one-quarter loginSpace">

            <div class="divInfo">
                <div class="imageLogo">
                    <figure class="image is-128x128">
                        <img src="https://bulma.io/assets/images/placeholders/128x128.png" />
                    </figure>
                </div>
                <div class="divInput">
                    <input class="input is-small" type="text" placeholder="Login/e-mail" />
                </div>
                <div class="divInput">
                    <input class="input is-small" type="text" placeholder="Senha" />
                </div>
                <div class="divInput">
                    <button class="button is-small is-primary" @click="fetchData">Logar</button>
                </div>
                {{ posts }}
                <div>
                    <p class="designed">Designed by André Alves Mesquita</p>
                </div>
            </div>
        </div>
    </div>
</template>



<script>
import axios from "axios"

export default {
    name: 'Login',
    props: ['updateParentValue'],
    data() {
        return {
            posts: null
        }
    },
    methods: {
        logar() {
            this.$emit('click', true);
        },
        fetchData() {
            axios.get('http://localhost:3000/')
                .then(response => {
                    this.posts = response.data;
                })
                .catch(error => {
                    console.log('Error fetching data:', error);
                });
        }

    },
    computed: {

    }
}
</script>


<style>
.divInfo {
    width: 100%;
}

.imageLogo {
    display: flex;
    justify-content: center;
}

.designed {
    margin-top: 60px;
    font-size: 12px;
    text-align: center;
}

.divInput {
    margin: 20px;
}

.divFull {
    height: 100%;
}

.zeroMP {
    margin: 0;
    padding: 0
}

.fundoImagem {
    height: 100%;
    background-image: url('https://source.unsplash.com/random');
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
}

.loginSpace {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>