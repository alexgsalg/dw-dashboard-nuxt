<template>
  <div class="main_wrapper">
    <ActionBar title="Resultados" />

    <div class="results">
      <!-- Filtros -->
      <form action="" class="results_filter" :class="{ open: filterOpen }">
        <div class="wrapper">
          <div class="results_header">
            <h3 class="results__title">Filtros</h3>
            <i
              class="fas fa-times filter_close"
              @click="filterOpen = false"
            ></i>
          </div>
          <div class="filter_box">
            <!-- Filtros item -->
            <div class="filter_box__item">
              <div class="filter_box__itemtop">
                <p class="filter_box__title">Preços</p>
              </div>
              <label
                v-for="item in radio"
                :key="item.valor"
                class="radio"
                @click="priceSelected = item.value"
              >
                {{ item.text }}
                <input
                  type="radio"
                  name="prices"
                  :value="item.value"
                  :checked="item.value == priceSelected"
                />
                <span class="checkround"></span>
              </label>
            </div>

            <div class="filter_box__item">
              <div class="filter_box__itemtop">
                <p class="filter_box__title">Valores</p>
                <p class="filter_box__title">
                  R${{ sliderRange.value[0] }} - R${{ sliderRange.value[1] }}
                </p>
              </div>
              <b-form-slider
                id="valorRange"
                v-model="sliderRange.value"
                :value="sliderRange.value"
                :min="sliderRange.min"
                :max="sliderRange.max"
              ></b-form-slider>
            </div>

            <div class="filter_box__item">
              <div class="filter_box__itemtop">
                <p class="filter_box__title">Categorias</p>
              </div>

              <label v-for="item in check" :key="item.valor" class="check">
                {{ item.text }}
                <input
                  type="checkbox"
                  name="category"
                  :value="item.value"
                  :checked="item.ischecked"
                  @click="item.ischecked = !item.ischecked"
                />
                <span class="checkmark"></span>
                <span class="counter">{{ item.counter }}</span>
              </label>
            </div>

            <div class="filter_box__item last">
              <div class="filter_box__itemtop">
                <p class="filter_box__title">Avaliação</p>
              </div>

              <label class="rating">
                <input
                  type="radio"
                  name="rating"
                  :value="rating[0].value"
                  :checked="ratingSelected == rating[0].value"
                  @click="ratingSelected = rating[0].value"
                />
                <five-star-icon />
                <span class="counter">{{ rating.five }}</span>
              </label>

              <label class="rating">
                <input
                  type="radio"
                  name="rating"
                  :value="rating[1].value"
                  :checked="ratingSelected == rating[1].value"
                  @click="ratingSelected = rating[1].value"
                />
                <four-star-icon />
                <span class="counter">{{ rating.five }}</span>
              </label>

              <label class="rating">
                <input
                  type="radio"
                  name="rating"
                  :value="rating[2].value"
                  :checked="ratingSelected == rating[2].value"
                  @click="ratingSelected = rating[2].value"
                />
                <three-star-icon />
                <span class="counter">{{ rating.five }}</span>
              </label>
            </div>
            <div class="filter_box__btn">
              <button type="button" class="btn filter_btn" @click="clearFilter">
                Limpar filtros
              </button>
            </div>
          </div>
        </div>
      </form>
      <div class="results_list">
        <form action="" class="results_search">
          <div class="results_header">
            <h3 class="results__title">200 resultados encontrados</h3>
            <div class="results_organize">
              <select id="listagem" name="listagem">
                <option value="asc" hidden>Listagem</option>
                <option value="asc">Crescente</option>
                <option value="des">Decrescente</option>
                <option value="des">Maior Valor</option>
                <option value="des">Menor Valor</option>
              </select>

              <!-- Botão de grid card -->
              <button class="organize_btn" @click="changeToCard">
                <grid-card />
              </button>

              <!-- Botão de grid list -->
              <button class="organize_btn" @click="changeToList">
                <list-card />
              </button>

              <a
                href="#"
                class="organize_filterMobile"
                @click="filterOpen = true"
              >
                <i class="fas fa-sliders-h"></i>
              </a>
            </div>
          </div>
          <div class="searchbox">
            <input id="search" type="text" name="search" placeholder="Buscar" />
            <button type="submit">
              <img
                src="../assets/img/icon-search.svg"
                alt="íconde de pesquisa"
              />
            </button>
          </div>
        </form>
        <div class="results_cards" :class="{ blinkIn: blinkIn }">
          <!-- CARD ITEM -->
          <div
            v-for="curso in cursos"
            :key="curso.id"
            class="card_item"
            :class="{ toCard: changeGrid }"
          >
            <a :href="curso.id" class="card_item__img"
              ><img
                :src="
                  'http://localhost:1337' +
                  curso.Imagem[0].formats.thumbnail.url
                "
                alt="Imagem de card"
            /></a>

            <div class="card_item__content">
              <h3 class="card_item__title">
                <a href="#">{{ curso.Nome }}</a>
              </h3>
              <p class="card_item__by"><span>Por</span> {{ curso.Autor }}</p>
              <p class="card_item__text">
                {{ curso.Descricao.substring(0, 200) + '...' }}
              </p>
            </div>
            <div class="card_item__info">
              <div>
                <span class="card_item__rating">
                  {{ curso.Avaliacao }}
                  <img src="../assets/img/star-outline.png" alt="rating" />
                </span>
                <p class="card_item__price">R${{ curso.Preco }}</p>
              </div>
              <div>
                <button type="button" class="btn btn_medium btn_light">
                  <i class="far fa-heart"></i>Amei
                </button>
                <a :href="curso.id" class="btn btn_medium">
                  <img
                    src="../assets/img/shopping-bag.svg"
                    alt="rating"
                  />Comprar
                </a>
              </div>
            </div>
          </div>
          <!-- Fim card -->
        </div>
      </div>
    </div>
    <Pagination />
  </div>
</template>

<script>
import bFormSlider from 'vue-bootstrap-slider/es/form-slider'
import axios from 'axios'
import GridCard from '../assets/icons/GridCard.vue'
import ListCard from '../assets/icons/ListCard.vue'
import FiveStarIcon from '../assets/icons/FiveStarIcon.vue'
import FourStarIcon from '../assets/icons/FourStarIcon.vue'
import ThreeStarIcon from '../assets/icons/ThreeStarIcon.vue'

export default {
  name: 'Cursos',
  components: {
    GridCard,
    ListCard,
    FiveStarIcon,
    FourStarIcon,
    ThreeStarIcon,
    bFormSlider,
    // VueRangeSlider,
  },
  data: () => ({
    changeGrid: false,
    blinkIn: false,
    filterOpen: false,
    cursos: [],
    radio: [
      { text: 'Todos', value: 'all' },
      { text: 'R$50', value: '50' },
      { text: 'R$50-R$100', value: '50_100' },
      { text: 'R$100-R$500', value: '100_500' },
      { text: 'R$500', value: '500' },
    ],
    priceSelected: 'all',
    check: [
      {
        text: 'Metodologias',
        value: 'metodos',
        ischecked: false,
        counter: 1920,
      },
      {
        text: 'Desenvolvimento',
        value: 'desenvolvimento',
        ischecked: false,
        counter: 1820,
      },
      {
        text: 'Programação',
        value: 'programcao',
        ischecked: false,
        counter: 462,
      },
      {
        text: 'Audiovisual',
        value: 'video',
        ischecked: false,
        counter: 6556,
      },
    ],
    rating: [
      { five: 8500, value: '5' },
      { four: 3250, value: '4' },
      { three: 1120, value: '3' },
    ],
    ratingSelected: 'false',

    sliderRange: {
      id: 'valorRange',
      value: [10, 1000],
      max: 1000,
      min: 0,
      tooltip: 'hide',
      ticks_tooltip: false,
    },

    cards: [
      {
        id: 0,
        link: '#',
        image: require('../assets/img/metodoAgil.jpg'),
        title: 'Formula ágil',
        by: 'Leo Cordeiro',
        price: '500',
        rating: '4.3',
        content:
          "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a typespecimen book.",
      },
      {
        id: 1,
        link: '#',
        image: require('../assets/img/flexGrid.png'),
        title: 'Flexbox e CSSGrid',
        by: 'Alex Salgado',
        price: '2000',
        rating: '4.9',
        content:
          "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a typespecimen book.",
      },
      {
        id: 2,
        link: '#',
        image: require('../assets/img/responsive.jpg'),
        title: 'Responsividade crossbrowser',
        by: 'Sergio Moura',
        price: '2500',
        rating: '5.0',
        content:
          "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a typespecimen book.",
      },
      {
        id: 3,
        link: '#',
        image: require('../assets/img/audioMastering.jpg'),
        title: 'Gravação e masterização',
        by: 'Brasil Play',
        price: '2500',
        rating: '4.0',
        content:
          "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a typespecimen book.",
      },
    ],
  }),

  async mounted() {
    try {
      const response = await axios.get('http://localhost:1337/cursos')
      this.cursos = response.data
    } catch (error) {
      this.error = error
    }
  },
  methods: {
    changeToCard(event) {
      event.preventDefault()
      if (this.changeGrid === false) {
        this.blinkIn = true
        setTimeout(() => {
          this.changeGrid = true
        }, 300)
        setTimeout(() => {
          this.blinkIn = false
        }, 500)
      }
    },
    changeToList(event) {
      event.preventDefault()
      if (this.changeGrid === true) {
        this.blinkIn = true
        setTimeout(() => {
          this.changeGrid = false
        }, 160)
        setTimeout(() => {
          this.blinkIn = false
        }, 500)
      }
    },
    clearFilter() {
      this.check.map((item) => {
        return (item.ischecked = false)
      })
      this.priceSelected = 'all'
      this.ratingSelected = ''
      this.sliderRange.value = [0, 1000]
      this.filterOpen = false
    },
    ifMobile() {
      if (window.innerWidth < 780) {
        this.cards.map((item) => {
          return item.content.substring(0, 10) + '..'
        })
      }
    },
  },
}
</script>
<style lang="scss">
@import 'bootstrap-slider/dist/css/bootstrap-slider.css';
</style>
