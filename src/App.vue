<template>
  <div class="container">
    <button class="start-button" @click="openPopup">Начать</button>
    <div v-show="isPopupOpen" class="popup-overlay" @click.self="closePopup">
      <div class="popup">
        <h2>Попап</h2>
        <div class="form">
          <div class="form-row">
            <label for="name">Имя:</label>
            <input type="text" id="name" v-model="formData.name" />
          </div>
          <div class="form-row">
            <label for="email">Email:</label>
            <input type="email" id="email" v-model="formData.email" />
          </div>
          <div class="form-row">
            <label for="phone">Телефон:</label>
            <input type="tel" id="phone" v-model="formData.phone" />
          </div>
          <div class="form-row">
            <label for="address">Адрес:</label>
            <input type="text" id="address" v-model="formData.address" />
          </div>
          <div class="form-row">
            <label for="message">Сообщение:</label>
            <textarea id="message" v-model="formData.message"></textarea>
          </div>
          <button @click="submitForm">Отправить</button>
        </div>
      </div>
    </div>
    <div class="data">
      <h2>Введенные данные:</h2>
      <pre>{{ conclusion }}</pre>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isPopupOpen: false,
      formData: {
        name: "",
        email: "",
        phone: "",
        address: "",
        message: "",
      },
      conclusion: [],
    };
  },
  methods: {
    openPopup() {
      this.isPopupOpen = true;
    },
    closePopup() {
      this.isPopupOpen = false;
    },
    submitForm() {
      this.conclusion.push(this.formData);
      this.formData = {
        name: "",
        email: "",
        phone: "",
        address: "",
        message: "",
      };
      this.closePopup();
    },
  },
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
}

.start-button {
  font-size: 24px;
  padding: 12px 24px;
}

.popup-overlay {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 999;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.popup {
  max-width: 500px;
  background-color: white;
  padding: 24px;
}

.form {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.form-row {
  width: calc(50% - 8px);
  margin-bottom: 16px;
}

label {
  display: block;
  margin-bottom: 8px;
}

input,
textarea {
  width: 100%;
  padding: 8px;
}

button {
  font-size: 18px;
  padding: 12px 24px;
  margin-top: 16px;
}

.data {
  margin-top: 24px;
  width: 100%;
  max-width: 500px;
  padding: 24px;
  background-color: #f5f5f5;
}
</style>
