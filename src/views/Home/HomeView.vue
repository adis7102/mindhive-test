<template>
  <div class="home">
    <div class="home-product">
      <div v-if="productData" class="home-product-wrap">
        <div class="navbar-product">
          <img src="@/assets/images/arrow.png" alt="arrow" />
          <p>Clothing</p>
        </div>
        <div class="title-product">
          <p>{{ productData.title }}</p>
        </div>
        <div class="price-product">
          <p>${{ productData.price }}</p>
        </div>
        <div class="image-product">
          <img :src="productData.image" alt="image product" />
        </div>
      </div>
      <div v-else class="loading-product">Loading product ...</div>
    </div>
    <div class="home-form">
      <div class="home-form-wrap">
        <Button
          title="Pay"
          width="100%"
          height="50px"
          color="white"
          backgroundColor="black"
          :withAppleICon="true"
        />
        <div class="pay-divider">
          <div class="pay-divider-text">
            <p>Or pay with card</p>
          </div>
        </div>
        <p class="detail-form-text">Shipping Information</p>
        <div class="email-input">
          <p>Email</p>
          <p>{{ formInput.email }}</p>
          <input v-model="formInput.email" />
        </div>
        <div class="shipping-addres-input">
          <p class="shipping-addres-input-title">Shipping address</p>
          <div class="input-card">
            <div class="dropdown">
              <select v-model="formInput.country" name="country">
                <option v-for="option in options" :value="option.value">
                  {{ option.title }}
                </option>
              </select>
            </div>
            <div class="input-card-input-text">
              <input v-model="formInput.name" name="username" placeholder="Name" />
            </div>
            <div class="input-card-input-text">
              <input v-model="formInput.address" name="address" placeholder="Address" />
            </div>
          </div>
          <p class="enter-address-manually">Enter address manually</p>
        </div>
        <p class="detail-form-text">Payment Details</p>
        <div class="card-information-form">
          <p class="card-information-form-title">Card information</p>
          <div class="card-information-form-card">
            <div class="card-information-form-card-input with-card">
              <input
                maxlength="19"
                type="number"
                oninput="this.value=this.value.slice(0,this.maxLength)"
                name="cardNumber"
                placeholder="1234 1234 1234 1234"
                v-model="formInput.cardNumber"
              />
              <div class="cards-provider">
                <img
                  class="visa-card"
                  src="@/assets/images/visa.png"
                  alt="visa"
                />
                <img
                  class="master-card"
                  src="@/assets/images/mastercard.png"
                  alt="mastercard"
                />
              </div>
            </div>
            <div class="card-information-form-card-input flex-input">
              <div class="flex-input-wrap date-input">
                <input
                  maxlength="2"
                  type="number"
                  oninput="this.value=this.value.slice(0,this.maxLength)"
                  name="month"
                  placeholder="MM"
                  v-model="formInput.month"
                />
                /
                <input
                  maxlength="2"
                  type="number"
                  oninput="this.value=this.value.slice(0,this.maxLength)"
                  name="year"
                  placeholder="YY"
                  v-model="formInput.year"
                />
              </div>
              <div class="flex-input-wrap cvc-input">
                <input
                  maxlength="3"
                  type="number"
                  oninput="this.value=this.value.slice(0,this.maxLength)"
                  name="cvc"
                  placeholder="CVC"
                  v-model="formInput.cvc"
                />
                <img class="cvc-card" src="@/assets/images/cvc.png" alt="cvc" />
              </div>
            </div>
          </div>
        </div>
        <div class="billing-address-check">
          <input type="checkbox" name="billingAddressCheck" value="true" />
          <label for="vehicle1">Billing address is same as shipping</label>
        </div>
        <Button
          title="Pay $65.00"
          width="100%"
          height="50px"
          color="white"
          backgroundColor="black"
        />
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import "./styles.scss";
import Button from "@/components/Button/Button.vue";

export default {
  components: { Button },
  name: "HomeView",
  data() {
    return {
      productData: null,
      options: [
        { title: "United States", value: "US" },
        { title: "Indonesia", value: "ID" },
      ],
      formInput: {
        email: '',
        country: '',
        name: '',
        address: '',
        cardNumber: '',
        month: '',
        year: '',
        cvc: ''
      },
      isValid: false
    };
  },
  mounted() {
    fetch("https://fakestoreapi.com/products/1", {
      method: "GET",
    })
      .then((res) => res.json())
      .then((data) => {
        this.productData = data;
      })
      .catch((e) => console.error(e));
  },
};
</script>
