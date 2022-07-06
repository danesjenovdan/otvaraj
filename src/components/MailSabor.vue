<script setup>
import { ref } from 'vue'

defineProps({
  show: Boolean,
})

</script>

<template>
  <div class="mail" :class="{ 'show': show }">
    <div class="line">
      <label for="receiver">To:</label>
      <input type="email" name="receiver" value="predsjednik@sabor.hr" />
    </div>
    <div class="line">
      <label for="subject">Subject:</label>
      <input type="text" name="subject" value="Otvorite Sabor, maknite barikade" />
    </div>
    <div class="line">
      <textarea rows="20">
Poštovani predsjedniče Hrvatskog sabora, gospodine Jandrokoviću

Sa željom da se glas građanki i građana čuje i uvaži, a rad demokratskih institucija bude vidljiv, transparentan i otvoren, Gong apelira da otvorite Sabor kako bi nas više i bolje informirali o tome što radite i kvalitetnije uključili u procese donošenja odluka.

Želimo Sabor koji je otvoren građanskim inicijativama, suradljiv i odgovoran prema svojoj predstavničkoj funkciji.

Imamo pravo znati i pratiti koliko odgovorno obavljate svoje javne dužnosti, s kime se sastajete i savjetujete prilikom donošenja odluka. Tražimo da osigurate nesmetan rad neovisnih institucija i osnažite ih u cilju zaštitite ljudskih prava i građanskih sloboda ali i prava na slobodan pristup informacijama i preispitivanje odluka i postupaka izabranih vlasti.

Ljubazno Vas molimo da učinite koliko je u Vašoj moći da vratite povjerenje građana u temeljne demokratske institucije:

- maknite barikade s Markova trga
- poštujte građanke i građane kojima služite tako da od njih ne skrivate što radite
- poštujte funkciju za koju ste izabrani time što ćete otvoreno izložiti svoju imovinu, osobne interese i svoj rad javnosti, te prijaviti i objaviti svaki dar i svaki sastanak s lobistima
- poštujte novinarke i novinare i vratite redovne konferencije na kojima vam mogu postavljati pitanja od javnog interesa
- otvorite zatvorene sjednice Vlade ili bar jasno propišete, a možda se i savjetujete s javnošću o tome koje vrste odluka se raspravljaju zatvoreno od javnosti
- otvorite javne rasprave o hrvatskim stajalištima u europskim politikama, i svakako da stajališta prestanete donositi na zatvorenom dijelu sjednica Vlade
- osnažite neovisne institucije koje nadziru vaš rad i prihvatite odgovornost za poštivanje načela djelovanja o kršenju kojih bi moralo odlučivati neovisno tijelo

S poštovanjem,
      </textarea>
    </div>
  </div>
</template>

<style scoped>

.mail {
  left: 20px;
  right: 20px;
  top: -100vh;
  position: absolute;
  z-index: 1001;
  background-color: white;
  box-sizing: border-box;
  padding: 20px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
  font-family: 'Archivo', sans-serif;
  width: 80%;
  transition: all 0.5s ease;
}

.mail label {
  padding-right: 10px;
}

.mail .line {
  margin-bottom: 15px;
  display: flex;
}

.mail .line input {
  flex-grow: 1;
}

.mail textarea {
  flex-grow: 1;
}

.mail.show {
  top: 20px;
}

@media (min-width: 992px) {
  .mail {
    margin-left: auto;
    margin-right: auto;
    left: 0;
    right: 0;
    width: 50%;
    padding: 40px;
  }
}
</style>