<script setup>
import { ref } from 'vue'

defineProps({
  show: Boolean,
  showContentFor: String
})

const otvaraj = ref(false)
const sendMessage = ref(false)

function chooseAction(action) {
  console.log('Acction', action)
  otvaraj.value = true
  sendMessage.value = action
}

</script>

<template>
  <div class="sidebar">
    <img alt="Parlametar logo" src="../assets/logo-parlameter.png" />
    <div v-if="showContentFor === 'parliament'">
      <h1>Što i koliko radi tvoja zastupnik_ca?</h1>
      <p>Tijekom dvije pandemijske godine Sabor je prestao objavljivati poimenične rezultate glasanja, nema podataka o tome dolaze li zastupnici i zastupnice na posao u Sabor, koliko i kako sudjeluju na sjednicama radnih tijela i što tamo govore. Iznimno, ako predsjednik radnog tijela odluči da će sjednicu prenositi na YouTube kanalu Sabora, i ako je dvorana opremljena za video-prijenos, to će ipak ostati zabilježeno i dostupno za pregled na YouTube kanalu Sabora.</p>
      <h3>> Zašto bi nas trebale zanimati sjednice radnih tijela Sabora?</h3>
      <p>Na sjednicama radnih tijela provode se javna saslušanja poput onoga za predsjednicu, a na koncu predsjednika Vrhovnog sude Hrvatske, glavnu državnu odvjetnicu, ministre u Vladi i ostale funkcije koje mora potvrditi saborska većina. Dakle, to nije inkvizicija kako ju naziva premijer Plenković, već poslovnički instrument kojim Sabor vrši svoju nadzornu funkciju. Dodatno, na sjednicama radnih tijela sudjeluju vanjski članovi čije ćete mišljenje malo kada pronaći u zaključcima koje Sabor objavljuje na službenoj stranici, s obzirom kako se transkripti i cjeloviti zapisnici ne objavljuju.</p>
      <h3>> Što ako imam pitanje za zastupnicu_ka?</h3>
      <p>Provjeri na Parlametru ako ima profil na društvenim mrežama jer Sabor ne objavljuje email adrese na koje bi se mogli obratiti izravno zastupnici_ku. Nema ni redovnih termina rezerviranih za primanje građanki i građana, a osim organiziranja referenduma, nema drugog mehanizma da građanke i građani obavežu Sabor da razmotri njihove prijedloge i mišljenja.</p>
      <a href="https://gong.hr/2022/05/05/gongove-preporuke-saboru-otvorite-svoj-rad-gradankama/" target="_blank">#OTVARAJ</a>
    </div>
    <div v-if="showContentFor === 'government'">
      <h1>Jel’ otvoreno?</h1>
      <p>Ako je vlast otvorena građani mogu više sudjelovati u javnom životu, smanjuje se prostor za korupciju i bolje se štite prava građana. Ako je vlast otvorena, znači da građani nisu u mraku.</p>
      <h3>Znači li to da mogu na sjednicu?</h3>
      <p>Ne može se baš na sjednicu, ali dostupan je prijenos i snimka na službenoj stranici Vlade. O čemu će raspravljati na sjednici, to Vlada objavljuje koji sat prije početka, a u svakom trenutku može odlučiti zatvoriti raspravu za javnost. Pored toga, baš svaku sjednicu Vlada zaključuje dijelom zatvorenim za javnost gdje onda raspravljaju o hrvatskim stajalištima kod donošenja EU politika i drugim europskim poslovima, robnim rezervama, kadroviranju, dodjeli sredstava i tome slično.</p>
      <h3>Što ako sam novinar_ka?</h3>
      <p>Onda dočekuješ ministre ispred Banskih dvora, tako je barem bilo dok se još moglo do Markovog trga. Uglavnom, redovne konferencije za javnost na kojima bi novinari mogli postavljati pitanja, toga nema. Recimo Stožer ih je imao za vrijeme trajanja epidemioloških mjera. Vlada zadnji put još kad je Ivica Račan bio premijer.</p>
      <a href="https://gong.hr/2022/03/28/gong-vladi-otvorite-markov-trg-i-svoj-rad-javnosti/" target="_blank">#OTVARAJ</a>
    </div>
    <div v-if="showContentFor === 'police'">
      <h1>Ti bi na Markov trg?</h1>
      <p>Po Markovom trgu ne možete prošetati već godinu i više dana, jer iza barikada pristup je dozvoljen samo ako ste najavljeni da dolazite na sastanak u Sabor ili Vladu ili ste najavili okupljanje. Policija pri tom provjerava osobni dokument i jeste li najavljeni, ali ne vodi evidenciju o tome tko se, kada i zašto kretao štićenim prostorom 1. Kategorije. Tako su nam barem rekli kada smo ih temeljem prava na pristup informacijama tražile tu evidenciju.</p>
      <a href="https://gong.hr/2022/05/24/vlada-dvije-godine-ne-dozvoljava-gradankama-na-markov-trg-mup-odgovara-bas-nas-briga-tko-tamo-prolazi/" target="_blank">#OTVARAJ</a>
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
        <button @click="chooseAction(true)">#OTVARAJ</button>
        <button @click="chooseAction(false)">Nebitno</button>
      </div>
      <div v-else>
        aaa
        <div v-if="sendMessage">
          <p>Čestitamo! Zato što ne odustajete od svojeg prava da kritički preispitujete rad demokratskih institucija, pozivate na odgovornost dužnosnika i uporno tražite da bolje služe društvu. Uključite se, pošaljite poruku Vladi i Saboru, vrijeme je da uvaže i naše mišljenje.</p>
          <a href="/">Piši Saboru i Vladi</a>
        </div>
        <div v-else>
          <p>Žao nam je ako ste potonuli u političku apatiju ili mislite kako je život prekratak za borbu s vjetrenjačama, ali sjetite se pandemije i prijedloga o praćenju mobitela koji srećom u Saboru nije prošao. Zato, i ako vam je nebitno, pomislite na druge, jer država pripada svima nama. Uključite se, pošaljite poruku Vladi i Saboru.</p>
          <a href="/">Piši Saboru i Vladi</a>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.sidebar {
  position: absolute;
  z-index: 1000;
  background-color: white;
  /* border-right: 1px solid black; */
  width: 300px;
  height: 100%;
  min-height: 100%;
  box-sizing: border-box;
  overflow-y: scroll;
  padding: 10px;
}
</style>
