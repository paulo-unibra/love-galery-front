    <script setup lang="ts">
    import 'vue3-carousel/carousel.css'
    import { Carousel, Slide } from 'vue3-carousel'

    const carouselConfig = {
        itemsToShow: 5.5,
        wrapAround: false,
        snapAlign: 'start', // Alinha os itens ao início, reduzindo o espaço entre eles
        breakpoints: {
            1200: {
                itemsToShow: 4.5,
            },
            992: {
                itemsToShow: 3.5,
            },
            768: {
                itemsToShow: 2.5,
            },
            0: {
                itemsToShow: 3.1, // Exibir 3.5 itens no mobile
            }
        }
    }

    const carouselMainConfig = {
        itemsToShow: 3.2, // Deixe sempre um pedaço dos itens laterais visíveis
        snapAlign: 'center',
        wrapAround: true, // Para evitar corte nos extremos
        autoplay: 10000,
        // transition: 50,
        breakpoints: {
            1200: { itemsToShow: 2.5, snapAlign: 'center' },
            992: { itemsToShow: 2.2, snapAlign: 'center' },
            768: { itemsToShow: 1.8, snapAlign: 'center' },
            0: { itemsToShow: 1.1, snapAlign: 'center' } // Mobile: um item maior, com bordas visíveis
        }
    }

</script>

    <template>
        <Carousel v-bind="carouselMainConfig">
            <Slide v-for="(slide, index) in [{
                image: 'https://lh3.googleusercontent.com/pw/AP1GczNE-bV-jOopb5uiFF2K3I1RlwTtUjal2FZ1CXyhJpw4vsKVq46S59Eg3LnmBS8g2TjO6FGAi5ZKw85VQt1i12G3kOzoI0zmKklCU0qVmsX75qDtTx-CQuQDtLCX-4QBLytUiA1xNFzMCoHYhlyUXpBsXg=w521-h927-s-no-gm?authuser=0'
            },
            {
                image: 'https://lh3.googleusercontent.com/pw/AP1GczMUDROhqcfj1tpFTZneQ2tbAdPLuXchRuxIqf9wich1pN9DlyNKF7yMoFTQy4Vj_f42m_gHB_ANSKbD97hLTH5g20S3N1JbjcNfpIY4v11mLLrwY3Ub5nhiff0wnLy7Xjs3CwctzSxmwhs9ndHsn14HLg=w521-h927-s-no-gm?authuser=0'
            },
            {
                image: 'https://lh3.googleusercontent.com/pw/AP1GczPYuMPBR2MYD7fQYRorh7RC-U08Nhv3pe2sPVxtsQ0DOKN0PQMWlLg_pJvJASwcEGbM1zEi16R4px6feK6FVoCKwa5hLJfXL0km2zurltvaHmKTRoaFp7IqSbMRgYJc3GdvfK-bJhp1q3ekg9BPSEiSAA=w695-h927-s-no-gm?authuser=0'
            },
            {
                image: 'https://lh3.googleusercontent.com/pw/AP1GczNLYUSa966oI5ZXJKufycBwI7HkCjV38VoArC_k_tH9hqwfy-Rj38YRemhEgHwrr_nyMTBbDr3q_Bdwqyow8A3JdBNpbLlr3q6YspIueciq2cGluoQAAP8dzmz4zhxbdcdowExdcV7Q5O6vpM-pXepv4Q=w752-h927-s-no-gm?authuser=0'
            },
            {
                image: 'https://lh3.googleusercontent.com/pw/AP1GczMxe1aKwR2FYilyE7TTsX84WtnkEGP-3ny0MqNwCfgajbzcu0pj3eTY_2FilPSmVnlhcnNAqEkQRs_ydqMQ84R90ZNfFBsIJfYDk8iDZBzfw1kmuAAUbucJ5spKwGvLgpwx-HgzHoNL6QiiE0zm0F2_6w=w695-h927-s-no-gm?authuser=0'
            }
            ]" :key="index">
                <div class="main_carrousel_img" :style="{ backgroundImage: `url(${slide.image})` }">
                    <div class="button-container">
                        <button class="action-button transparent-text">VER AGORA</button>
                        <!-- <button class="action-button outline">+ MINHA LISTA</button> -->
                    </div>
                </div>
            </Slide>
        </Carousel>



        <h1 class="category_title">Quando nos conhecemos</h1>
        <Carousel v-bind="carouselConfig">
            <Slide v-for="slide in 10" :key="slide">
                <div src="https://placehold.co/300x450" alt="" class="img"></div>
            </Slide>
        </Carousel>

        <h1 class="category_title">O pedido de namoro</h1>
        <Carousel v-bind="carouselConfig">
            <Slide v-for="slide in 10" :key="slide">
                <div src="https://placehold.co/300x450" alt="" class="img"></div>
            </Slide>
        </Carousel>
    </template>

<style scoped>
.category_title {
    padding: 10px;
    font-size: 14px;
    font-weight: bolder;
    margin: 10px 0;
}

/* Estilos para os slides do carousel */
.carousel__slide {
    padding: 0 5px;
    /* Reduz o espaçamento entre os slides */
}

/* Estilos para o modo mobile */
@media (max-width: 768px) {
    .carousel__slide .main_carrousel_img {
        width: 100%;
        height: 80vh;
        border-radius: 3px;
        /* background-image: url('https://www.cnnbrasil.com.br/viagemegastronomia/wp-content/uploads/sites/5/2025/01/americanos-trocam-eua-por-uruguai-3.jpg?resize=768,1024'); */
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
    }


    .carousel__slide img {
        width: 80%;
        /* Reduz o tamanho das imagens */
        height: auto;
        /* Mantém a proporção */
        margin: 0 auto;
        /* Centraliza as imagens */
    }

    .carousel__slide .img {
        width: 100%;
        height: 160px;
        border-radius: 3px;
        background-image: url('https://www.cnnbrasil.com.br/viagemegastronomia/wp-content/uploads/sites/5/2025/01/americanos-trocam-eua-por-uruguai-1.jpg?w=1220&h=674&crop=1&quality=85');
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
    }


}

/* Container dos botões */
.button-container {
    display: flex;
    gap: 1rem;
    justify-content: center;
    align-items: center;
    margin-top: 1rem;
    position: absolute;
    bottom: 20px;
    right: 0;
    left: 0;
}

/* Botão padrão */
.action-button {
    background-color: #ffffff;
    /* Cor de fundo branca */
    color: #000000;
    /* Texto preto */
    border: none;
    border-radius: 25px;
    /* Borda arredondada */
    padding: 10px 20px;
    /* Espaçamento interno */
    font-size: 16px;
    /* Tamanho da fonte */
    font-weight: bold;
    /* Texto em negrito */
    cursor: pointer;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    /* Sombra suave */
    transition: background-color 0.3s, transform 0.2s;
    /* Animações suaves */
}

.action-button:hover {
    background-color: #f0f0f0;
    /* Alteração no hover */
    transform: translateY(-2px);
    /* Elevação ao passar o mouse */
}

/* Botão com contorno */
.action-button.outline {
    background-color: transparent;
    /* Fundo transparente */
    color: #ffffff;
    /* Texto branco */
    border: 2px solid #ffffff;
    /* Borda branca */
}

.action-button.outline:hover {
    background-color: rgba(255, 255, 255, 0.1);
    /* Fundo leve ao passar o mouse */
}
</style>