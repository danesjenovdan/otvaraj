<script setup>
import { ref } from 'vue'

defineProps({
  show: Boolean
})


</script>

<template>
  <div class="sidebar">
    <h1>Što i koliko radi tvoja zastupnik_ca?</h1>
    <p>Tijekom dvije pandemijske godine Sabor je prestao objavljivati poimenične rezultate glasanja, nema podataka o tome dolaze li zastupnici i zastupnice na posao u Sabor, koliko i kako sudjeluju na sjednicama radnih tijela i što tamo govore. Iznimno, ako predsjednik radnog tijela odluči da će sjednicu prenositi na YouTube kanalu Sabora, i ako je dvorana opremljena za video-prijenos, to će ipak ostati zabilježeno i dostupno za pregled na YouTube kanalu Sabora.</p>
    <h3>> Zašto bi nas trebale zanimati sjednice radnih tijela Sabora?</h3>
    <p>Na sjednicama radnih tijela provode se javna saslušanja poput onoga za predsjednicu, a na koncu predsjednika Vrhovnog sude Hrvatske, glavnu državnu odvjetnicu, ministre u Vladi i ostale funkcije koje mora potvrditi saborska većina. Dakle, to nije inkvizicija kako ju naziva premijer Plenković, već poslovnički instrument kojim Sabor vrši svoju nadzornu funkciju. Dodatno, na sjednicama radnih tijela sudjeluju vanjski članovi čije ćete mišljenje malo kada pronaći u zaključcima koje Sabor objavljuje na službenoj stranici, s obzirom kako se transkripti i cjeloviti zapisnici ne objavljuju.</p>
    <h3>> Što ako imam pitanje za zastupnicu_ka?</h3>
    <p>Provjeri na Parlametru ako ima profil na društvenim mrežama jer Sabor ne objavljuje email adrese na koje bi se mogli obratiti izravno zastupnici_ku. Nema ni redovnih termina rezerviranih za primanje građanki i građana, a osim organiziranja referenduma, nema drugog mehanizma da građanke i građani obavežu Sabor da razmotri njihove prijedloge i mišljenja.</p>
    <a href="/">#OTVARAJ</a>
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
