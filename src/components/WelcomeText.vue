<script setup>
import { ref } from 'vue'

</script>

<template>
    <div class="welcome">
        <p>
            Hej, pristup Saboru i Vladi <span>blokiran</span> je već skoro dvije godine, <span>klikni</span> na ogradu i zgrade Sabora i Vlade da <span>srušiš barikade</span>!
        </p>
    </div>

    <img alt="Parlametar logo" class="parlametar-logo" src="../assets/parlametar_logo.svg" />
</template>

<style scoped>

.welcome {
  left: 20px;
  right: 20px;
  top: 20px;
  position: absolute;
  z-index: 1001;
  background-color: white;
  box-sizing: border-box;
  padding: 20px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
  font-size: 18px;
  line-height: 22px;
  font-family: 'Archivo', sans-serif;
  font-weight: 800;
}


.welcome p {
    margin: 0;
}

.welcome p span {
    color: #d41010;
}

.parlametar-logo {
  display: none;
  max-width: 100px;
  left: 40px;
  bottom: 40px;
  position: absolute;
  z-index: 1001;
}

@media (min-width: 992px) {
  .welcome {
    left: 40px;
    right: unset;
    top: 40px;
    width: 360px;
    padding: 40px;
    font-size: 28px;
    line-height: 32px;
  }

  .parlametar-logo {
    display: block;
  }
}
</style>