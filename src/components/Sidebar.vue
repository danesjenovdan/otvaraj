<script setup>
import { ref } from 'vue'
import Accordion from './Accordion.vue'

defineProps({
  show: Boolean,
  showContentFor: String
})

const emit = defineEmits(['hide', 'hideWalls'])

const otvaraj = ref(false)
const sendMessage = ref(false)

function chooseAction(action) {
  otvaraj.value = true
  sendMessage.value = action
}

function hideWalls() {
  emit('hideWalls')
}

</script>

<template>
  <div class="sidebar" :class="{ 'show': show }">
    <div @click="emit('hide')" class="mobile-collapse-line"><span></span></div>
    <img alt="Parlametar logo" src="../assets/logo-parlameter.png" />
    <div v-if="showContentFor === 'parliament'">
      <h1>Što i koliko radi tvoja zastupnik_ca?</h1>
      <p>Tijekom dvije pandemijske godine Sabor je prestao objavljivati poimenične rezultate glasanja, nema podataka o tome dolaze li zastupnici i zastupnice na posao u Sabor, koliko i kako sudjeluju na sjednicama radnih tijela i što tamo govore. Iznimno, ako predsjednik radnog tijela odluči da će sjednicu prenositi na YouTube kanalu Sabora, i ako je dvorana opremljena za video-prijenos, to će ipak ostati zabilježeno i dostupno za pregled na YouTube kanalu Sabora.</p>
      <hr />
      <Accordion 
        :header-text="'Zašto bi nas trebale zanimati sjednice radnih tijela Sabora?'" 
        :body-text="'Na sjednicama radnih tijela provode se javna saslušanja poput onoga za predsjednicu, a na koncu predsjednika Vrhovnog sude Hrvatske, glavnu državnu odvjetnicu, ministre u Vladi i ostale funkcije koje mora potvrditi saborska većina. Dakle, to nije inkvizicija kako ju naziva premijer Plenković, već poslovnički instrument kojim Sabor vrši svoju nadzornu funkciju. Dodatno, na sjednicama radnih tijela sudjeluju vanjski članovi čije ćete mišljenje malo kada pronaći u zaključcima koje Sabor objavljuje na službenoj stranici, s obzirom kako se transkripti i cjeloviti zapisnici ne objavljuju.'"
      ></Accordion>
      <hr />
      <Accordion
        :header-text="'Što ako imam pitanje za zastupnicu_ka?'"
        :body-text="'Provjeri na Parlametru ako ima profil na društvenim mrežama jer Sabor ne objavljuje email adrese na koje bi se mogli obratiti izravno zastupnici_ku. Nema ni redovnih termina rezerviranih za primanje građanki i građana, a osim organiziranja referenduma, nema drugog mehanizma da građanke i građani obavežu Sabor da razmotri njihove prijedloge i mišljenja.'"
      ></Accordion>
      <a href="https://gong.hr/2022/05/05/gongove-preporuke-saboru-otvorite-svoj-rad-gradankama/" target="_blank" class="link-button">#OTVARAJ</a>
      <hr />
    </div>
    <div v-if="showContentFor === 'government'">
      <h1>Jel’ otvoreno?</h1>
      <p>Ako je vlast otvorena građani mogu više sudjelovati u javnom životu, smanjuje se prostor za korupciju i bolje se štite prava građana. Ako je vlast otvorena, znači da građani nisu u mraku.</p>
      <hr />
      <Accordion 
        :header-text="'Znači li to da mogu na sjednicu?'" 
        :body-text="'Ne može se baš na sjednicu, ali dostupan je prijenos i snimka na službenoj stranici Vlade. O čemu će raspravljati na sjednici, to Vlada objavljuje koji sat prije početka, a u svakom trenutku može odlučiti zatvoriti raspravu za javnost. Pored toga, baš svaku sjednicu Vlada zaključuje dijelom zatvorenim za javnost gdje onda raspravljaju o hrvatskim stajalištima kod donošenja EU politika i drugim europskim poslovima, robnim rezervama, kadroviranju, dodjeli sredstava i tome slično.'"
      ></Accordion>
      <hr />
      <Accordion 
        :header-text="'Što ako sam novinar_ka?'" 
        :body-text="'Onda dočekuješ ministre ispred Banskih dvora, tako je barem bilo dok se još moglo do Markovog trga. Uglavnom, redovne konferencije za javnost na kojima bi novinari mogli postavljati pitanja, toga nema. Recimo Stožer ih je imao za vrijeme trajanja epidemioloških mjera. Vlada zadnji put još kad je Ivica Račan bio premijer.'"
      ></Accordion>
      <a href="https://gong.hr/2022/03/28/gong-vladi-otvorite-markov-trg-i-svoj-rad-javnosti/" target="_blank" class="link-button">#OTVARAJ</a>
      <hr />
    </div>
    <div v-if="showContentFor === 'police'">
      <h1>Ti bi na Markov trg?</h1>
      <p>Po Markovom trgu ne možete prošetati već godinu i više dana, jer iza barikada pristup je dozvoljen samo ako ste najavljeni da dolazite na sastanak u Sabor ili Vladu ili ste najavili okupljanje. Policija pri tom provjerava osobni dokument i jeste li najavljeni, ali ne vodi evidenciju o tome tko se, kada i zašto kretao štićenim prostorom 1. Kategorije. Tako su nam barem rekli kada smo ih temeljem prava na pristup informacijama tražile tu evidenciju.</p>
      <a href="https://gong.hr/2022/05/24/vlada-dvije-godine-ne-dozvoljava-gradankama-na-markov-trg-mup-odgovara-bas-nas-briga-tko-tamo-prolazi/" target="_blank" class="link-button">#OTVARAJ</a>
      <hr />
    </div>
    <div v-if="showContentFor === 'church'">
      <div v-if="!otvaraj">
        <h1>Otvaraj!</h1>
        <p>Pozivamo Vladu i Sabor da razmotre naše preporuke i otvore se prema javnosti, izlože javnom propitivanju, zaštite svoj politički integritet i vrate povjerenje građana.</p>
        <p>Draga Vlado i Sabore vrijeme je da:</p>
        <ul>
          <li>maknete barikade s Markova trga</li>
          <li>poštujete građanke i građane kojima služite tako da od njih ne skrivate što radite</li>
          <li>poštujete funkciju za koju ste izabrani time što ćete otvoreno izložiti svoju imovinu, osobne interese i svoj rad javnosti, te prijaviti i objaviti svaki dar i svaki sastanak s lobistima</li>
          <li>poštujete novinarke i novinare i vratite redovne konferencije na kojima vam mogu postavljati pitanja od javnog interesa</li>
          <li>otvorite zatvorene sjednice Vlade ili bar jasno propišete, a možda se i savjetujete s javnošću o tome koje vrste odluka se raspravljaju zatvoreno od javnosti</li>
          <li>otvarate javne rasprave o hrvatskim stajalištima u europskim politikama, i svakako da stajališta prestanete donositi na zatvorenom dijelu sjednica Vlade</li>
          <li>osnažite neovisne institucije koje nadziru vaš rad i prihvatite odgovornost za poštivanje načela djelovanja o kršenju kojih bi moralo odlučivati neovisno tijelo</li>
        </ul>
        <p>Draga Vlado i Sabore</p>
        <button @click="chooseAction(true)" class="link-button">#OTVARAJ</button>
        <button @click="chooseAction(false)">Nebitno</button>
        <hr />
      </div>
      <div v-else>
        <div v-if="sendMessage">
          <p>Čestitamo! Zato što ne odustajete od svojeg prava da kritički preispitujete rad demokratskih institucija, pozivate na odgovornost dužnosnika i uporno tražite da bolje služe društvu. Uključite se, pošaljite poruku Vladi i Saboru, vrijeme je da uvaže i naše mišljenje.</p>
          <a href="mailto:someone@yoursite.com?subject=Pozivamo%20Vladu%20i%20Sabor%20da%20razmotre%20na%C5%A1e%20preporuke%20i%20otvore%20se%20prema%20javnosti%2C%20izlo%C5%BEe%20javnom%20propitivanju%2C%20za%C5%A1tite%20svoj%20politi%C4%8Dki%20integritet%20i%20vrate%20povjerenje%20gra%C4%91ana.&body=Draga%20Vlado%20i%20Sabore%20vrijeme%20je%20da%3A%0A-%20maknete%20barikade%20s%20Markova%20trga%0A-%20po%C5%A1tujete%20gra%C4%91anke%20i%20gra%C4%91ane%20kojima%20slu%C5%BEite%20tako%20da%20od%20njih%20ne%20skrivate%20%C5%A1to%20radite%0A-%20po%C5%A1tujete%20funkciju%20za%20koju%20ste%20izabrani%20time%20%C5%A1to%20%C4%87ete%20otvoreno%20izlo%C5%BEiti%20svoju%20imovinu%2C%20osobne%20interese%20i%20svoj%20rad%20javnosti%2C%20te%20prijaviti%20i%20objaviti%20svaki%20dar%20i%20svaki%20sastanak%20s%20lobistima%0A-%20po%C5%A1tujete%20novinarke%20i%20novinare%20i%20vratite%20redovne%20konferencije%20na%20kojima%20vam%20mogu%20postavljati%20pitanja%20od%20javnog%20interesa%0A-%20otvorite%20zatvorene%20sjednice%20Vlade%20ili%20bar%20jasno%20propi%C5%A1ete%2C%20a%20mo%C5%BEda%20se%20i%20savjetujete%20s%20javno%C5%A1%C4%87u%20o%20tome%20koje%20vrste%20odluka%20se%20raspravljaju%20zatvoreno%20od%20javnosti%0A-%20otvarate%20javne%20rasprave%20o%20hrvatskim%20stajali%C5%A1tima%20u%20europskim%20politikama%2C%20i%20svakako%20da%20stajali%C5%A1ta%20prestanete%20donositi%20na%20zatvorenom%20dijelu%20sjednica%20Vlade%0A-%20osna%C5%BEite%20neovisne%20institucije%20koje%20nadziru%20va%C5%A1%20rad%20i%20prihvatite%20odgovornost%20za%20po%C5%A1tivanje%20na%C4%8Dela%20djelovanja%20o%20kr%C5%A1enju%20kojih%20bi%20moralo%20odlu%C4%8Divati%20neovisno%20tijelo" class="link-button wide" @click="hideWalls">Piši Saboru i Vladi</a>
        </div>
        <div v-else>
          <p>Žao nam je ako ste potonuli u političku apatiju ili mislite kako je život prekratak za borbu s vjetrenjačama, ali sjetite se pandemije i prijedloga o praćenju mobitela koji srećom u Saboru nije prošao. Zato, i ako vam je nebitno, pomislite na druge, jer država pripada svima nama. Uključite se, pošaljite poruku Vladi i Saboru.</p>
          <a href="mailto:someone@yoursite.com?subject=Pozivamo%20Vladu%20i%20Sabor%20da%20razmotre%20na%C5%A1e%20preporuke%20i%20otvore%20se%20prema%20javnosti%2C%20izlo%C5%BEe%20javnom%20propitivanju%2C%20za%C5%A1tite%20svoj%20politi%C4%8Dki%20integritet%20i%20vrate%20povjerenje%20gra%C4%91ana.&body=Draga%20Vlado%20i%20Sabore%20vrijeme%20je%20da%3A%0A-%20maknete%20barikade%20s%20Markova%20trga%0A-%20po%C5%A1tujete%20gra%C4%91anke%20i%20gra%C4%91ane%20kojima%20slu%C5%BEite%20tako%20da%20od%20njih%20ne%20skrivate%20%C5%A1to%20radite%0A-%20po%C5%A1tujete%20funkciju%20za%20koju%20ste%20izabrani%20time%20%C5%A1to%20%C4%87ete%20otvoreno%20izlo%C5%BEiti%20svoju%20imovinu%2C%20osobne%20interese%20i%20svoj%20rad%20javnosti%2C%20te%20prijaviti%20i%20objaviti%20svaki%20dar%20i%20svaki%20sastanak%20s%20lobistima%0A-%20po%C5%A1tujete%20novinarke%20i%20novinare%20i%20vratite%20redovne%20konferencije%20na%20kojima%20vam%20mogu%20postavljati%20pitanja%20od%20javnog%20interesa%0A-%20otvorite%20zatvorene%20sjednice%20Vlade%20ili%20bar%20jasno%20propi%C5%A1ete%2C%20a%20mo%C5%BEda%20se%20i%20savjetujete%20s%20javno%C5%A1%C4%87u%20o%20tome%20koje%20vrste%20odluka%20se%20raspravljaju%20zatvoreno%20od%20javnosti%0A-%20otvarate%20javne%20rasprave%20o%20hrvatskim%20stajali%C5%A1tima%20u%20europskim%20politikama%2C%20i%20svakako%20da%20stajali%C5%A1ta%20prestanete%20donositi%20na%20zatvorenom%20dijelu%20sjednica%20Vlade%0A-%20osna%C5%BEite%20neovisne%20institucije%20koje%20nadziru%20va%C5%A1%20rad%20i%20prihvatite%20odgovornost%20za%20po%C5%A1tivanje%20na%C4%8Dela%20djelovanja%20o%20kr%C5%A1enju%20kojih%20bi%20moralo%20odlu%C4%8Divati%20neovisno%20tijelo" class="link-button wide" @click="hideWalls">Piši Saboru i Vladi</a>
        </div>
        <hr />
      </div>
    </div>
  </div>
</template>

<style scoped>
.sidebar {
  bottom: -100vh;
  position: absolute;
  z-index: 1000;
  background-color: white;
  width: 100vw;
  height: 90%;
  /* min-height: 100%; */
  box-sizing: border-box;
  overflow-y: scroll;
  padding: 10px 28px 28px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
  transition: all 0.5s ease;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
}

.sidebar.show {
  left: 0;
  bottom: 0;
}

.mobile-collapse-line {
  display: flex;
  justify-content: center;
  padding-bottom: 20px;
}

.mobile-collapse-line span {
  height: 3px;
  width: 20px;
  background-color: #a6a6a6;
  border-radius: 2px;
}

@media (min-width: 992px) {
  .sidebar {
    width: 430px;
    left: -430px;
    bottom: 0;
    padding: 28px;
    height: 100%;
    min-height: 100%;
    border-radius: 0;
  }

  .mobile-collapse-line {
    display: none;
  }
}

h1 {
  font-family: 'Archivo', sans-serif;
  margin-top: 30px;
  margin-bottom: 15px;
}

h3 {
  font-family: 'Archivo', sans-serif;
  font-weight: 600;
}

p, li {
  font-weight: 300;
  font-size: 18px;
  line-height: 26px;
}

hr {
  border-top: #a6a6a6;
  background-color: #a6a6a6;
}

button {
  border: 3px solid #258498;
  background-color: white;
  color: #258498;
  font-size: 24px;
  font-family: 'Archivo', sans-serif;
  font-weight: 600;
  line-height: 25px;
  padding: 12px 0;
  width: 180px;
  display: inline-flex;
  justify-content: center;
  text-decoration: none;
  margin: 15px 0;
  display: inline-block;
  cursor: pointer;
}

.link-button {
  background-color: #258498;
  border: 3px solid #258498;
  color: white;
  font-size: 24px;
  font-family: 'Archivo', sans-serif;
  font-weight: 800;
  line-height: 25px;
  padding: 12px 0;
  width: 180px;
  display: inline-flex;
  justify-content: center;
  text-decoration: none;
  margin: 15px 0;
}

.link-button:hover {
  background-color: white;
  color: #258498; 
}

button.link-button {
  margin-right: 10px;
}

.link-button.wide {
  width: 260px;
}

</style>
