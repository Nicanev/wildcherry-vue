<template>
  <div class="cart">
    <div class="cart__container">
      <div class="cart__block-cart">
        <div class="cart__up">
          <div class="cart__title">Корзина</div>
          <div class="cart__checkAll">
            <input type="checkbox" name="checkAll" id="checkAll" />
            <label for="checkAll">Выбрать всё</label>
          </div>
        </div>
        <ul class="cart__items">
          <li class="cart__item" v-for="product in products" :key="product">
            <div class="cart__item-info">
              <input type="checkbox" name="checkItem" />
              <img :src="product.image" />
              <div class="cart__item-text">
                <h1 class="cart__item-title">{{ product.name }}</h1>
                <h2>{{ product.category }}</h2>
              </div>
              <div class="cart__item-count">
                <button class="cart__btn-minus">-</button>
                1
                <button class="cart__btn-plus">+</button>
              </div>
            </div>
            <div class="cart__item-price">{{ product.price }} Р</div>
          </li>
        </ul>
      </div>
      <div class="cart__block-total">
        <div class="cart__total-des">
          <div class="cart__total-price">Итого <span>19 999 Р</span></div>
          <div class="cart__total-info">
            <div class="cart__total-info-item">
              Количество: 2 шт. <span>49 999 Р</span>
            </div>
            <div class="cart__total-info-item">
              Скидка <span>-20 000 Р</span>
            </div>
            <div class="cart__total-info-item">
              Доставка <span>Бесплатно</span>
            </div>
          </div>
        </div>
        <button class="cart__total-btn">Оплатить заказ</button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      products: [],
    };
  },
  mounted() {
    let cookie = this.$cookies.get("product");
    cookie = cookie.split(";");
    cookie.forEach((id) => {
      axios
        .get("http://wildcherry/public/api/product/" + id)
        .then((response) => this.products.push(response.data));
    });
  },
};
</script>

<style lang="scss">
.cart {
  input[type="checkbox"] {
    width: 2.2rem;
    height: 2.2rem;
    accent-color: #de3162;
  }
  &__container {
    display: flex;
    gap: 5rem;
  }
  &__total-btn {
    width: 100%;
    background-color: #de3162;
    color: white;
    padding: 2rem 0;
    border: 0;
    border-radius: 0.5rem;
    font-size: 1.4rem;
    font-weight: bold;
  }
  &__total-info-item {
    display: flex;
    justify-content: space-between;
    font-size: 1.6rem;
    margin-top: 1rem;
    color: #a0949b;
    span {
      color: #a0949b;
    }
  }
  &__block-total {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    width: 100%;
    padding: 2.5rem;
    border-radius: 1.5rem;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  }
  &__total-price {
    font-size: 2.4rem;
    font-weight: bold;
    span {
      font-weight: bold;
    }
    display: flex;
    justify-content: space-between;
  }

  &__block-cart {
    min-width: 110rem;
    border-radius: 1.5rem;
    padding: 2.5rem;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  }
  &__item-info {
    display: flex;
    align-items: center;
  }
  &__item-price {
    font-size: 1.8rem;
    font-weight: bold;
  }
  &__checkAll {
    display: flex;
    align-items: center;
    gap: 1rem;
    font-size: 1.4rem;
    padding-bottom: 2rem;
    width: 100%;
    border-bottom: 0.1rem solid #a0949b;
  }
  &__item-count {
    display: flex;
    align-items: center;
    gap: 1rem;
    font-size: 1.8rem;
  }
  &__btn-minus {
    border-radius: 50%;
    background-color: white;
    width: 4rem;
    font-size: 1.8rem;
    height: 4rem;
    border: 0.1rem solid #a0949b;
  }
  &__btn-plus {
    border-radius: 50%;
    background-color: white;
    width: 4rem;
    font-size: 1.8rem;
    height: 4rem;
    border: 0.1rem solid #a0949b;
  }
  &__up {
  }
  &__title {
    font-size: 2.4rem;
    font-weight: bold;
    margin-bottom: 2rem;
  }
  &__item-text {
    height: 100%;
    width: 50rem;
    display: flex;
    flex-direction: column;
    align-items: start;
    justify-content: start;
    h1 {
      font-size: 1.6rem;
      font-weight: bold;
    }
  }
  &__item {
    margin-top: 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    img {
      width: 10rem;
      height: 8rem;
    }
  }
}
</style>
