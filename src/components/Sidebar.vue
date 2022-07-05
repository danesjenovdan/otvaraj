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
const wallsFallen = ref(false)

function chooseAction(action) {
  otvaraj.value = true
  sendMessage.value = action
}

function hideWallsSabor(e) {
  if (!wallsFallen.value) {
    emit('hide')
    emit('hideWalls')
    setTimeout(() => {
      window.open('mailto:predsjednik@sabor.hr?subject=Otvorite%20Sabor%2C%20maknite%20barikade&body=Po%C5%A1tovani%20predsjedni%C4%8De%20Hrvatskog%20sabora%2C%20gospodine%20Jandrokovi%C4%87u%0A%0ASa%20%C5%BEeljom%20da%20se%20glas%20gra%C4%91anki%20i%20gra%C4%91ana%20%C4%8Duje%20i%20uva%C5%BEi%2C%20a%20rad%20demokratskih%20institucija%20bude%20vidljiv%2C%20transparentan%20i%20otvoren%2C%20Gong%20apelira%20da%20otvorite%20Sabor%20kako%20bi%20nas%20vi%C5%A1e%20i%20bolje%20informirali%20o%20tome%20%C5%A1to%20radite%20i%20kvalitetnije%20uklju%C4%8Dili%20u%20procese%20dono%C5%A1enja%20odluka.%0A%C5%BDelimo%20Sabor%20koji%20je%20otvoren%20gra%C4%91anskim%20inicijativama%2C%20suradljiv%20i%20odgovoran%20prema%20svojoj%20predstavni%C4%8Dkoj%20funkciji.%20%0AImamo%20pravo%20znati%20i%20pratiti%20koliko%20odgovorno%20obavljate%20svoje%20javne%20du%C5%BEnosti%2C%20s%20kime%20se%20sastajete%20i%20savjetujete%20prilikom%20dono%C5%A1enja%20odluka.%20Tra%C5%BEimo%20da%20osigurate%20nesmetan%20rad%20neovisnih%20institucija%20i%20osna%C5%BEite%20ih%20u%20cilju%20za%C5%A1titite%20ljudskih%20prava%20i%20gra%C4%91anskih%20sloboda%20ali%20i%20prava%20na%20slobodan%20pristup%20informacijama%20i%20preispitivanje%20odluka%20i%20postupaka%20izabranih%20vlasti.%0ALjubazno%20Vas%20molimo%20da%20u%C4%8Dinite%20koliko%20je%20u%20Va%C5%A1oj%20mo%C4%87i%20da%20vratite%20povjerenje%20gra%C4%91ana%20u%20temeljne%20demokratske%20institucije%3A%0A%0A-%20maknite%20barikade%20s%20Markova%20trga%0A-%20po%C5%A1tujte%20gra%C4%91anke%20i%20gra%C4%91ane%20kojima%20slu%C5%BEite%20tako%20da%20od%20njih%20ne%20skrivate%20%C5%A1to%20radite%0A-%20po%C5%A1tujte%20funkciju%20za%20koju%20ste%20izabrani%20time%20%C5%A1to%20%C4%87ete%20otvoreno%20izlo%C5%BEiti%20svoju%20imovinu%2C%20osobne%20interese%20i%20svoj%20rad%20javnosti%2C%20te%20prijaviti%20i%20objaviti%20svaki%20dar%20i%20svaki%20sastanak%20s%20lobistima%0A-%20po%C5%A1tujte%20novinarke%20i%20novinare%20i%20vratite%20redovne%20konferencije%20na%20kojima%20vam%20mogu%20postavljati%20pitanja%20od%20javnog%20interesa%0A-%20otvorite%20zatvorene%20sjednice%20Vlade%20ili%20bar%20jasno%20propi%C5%A1ete%2C%20a%20mo%C5%BEda%20se%20i%20savjetujete%20s%20javno%C5%A1%C4%87u%20o%20tome%20koje%20vrste%20odluka%20se%20raspravljaju%20zatvoreno%20od%20javnosti%0A-%20otvorite%20javne%20rasprave%20o%20hrvatskim%20stajali%C5%A1tima%20u%20europskim%20politikama%2C%20i%20svakako%20da%20stajali%C5%A1ta%20prestanete%20donositi%20na%20zatvorenom%20dijelu%20sjednica%20Vlade%0A-%20osna%C5%BEite%20neovisne%20institucije%20koje%20nadziru%20va%C5%A1%20rad%20i%20prihvatite%20odgovornost%20za%20po%C5%A1tivanje%20na%C4%8Dela%20djelovanja%20o%20kr%C5%A1enju%20kojih%20bi%20moralo%20odlu%C4%8Divati%20neovisno%20tijelo%0A%0AS%20po%C5%A1tovanjem%2C%0A', '_blank')
    }, 2000)
    wallsFallen.value = true
  } else {
    window.open('mailto:predsjednik@sabor.hr?subject=Otvorite%20Sabor%2C%20maknite%20barikade&body=Po%C5%A1tovani%20predsjedni%C4%8De%20Hrvatskog%20sabora%2C%20gospodine%20Jandrokovi%C4%87u%0A%0ASa%20%C5%BEeljom%20da%20se%20glas%20gra%C4%91anki%20i%20gra%C4%91ana%20%C4%8Duje%20i%20uva%C5%BEi%2C%20a%20rad%20demokratskih%20institucija%20bude%20vidljiv%2C%20transparentan%20i%20otvoren%2C%20Gong%20apelira%20da%20otvorite%20Sabor%20kako%20bi%20nas%20vi%C5%A1e%20i%20bolje%20informirali%20o%20tome%20%C5%A1to%20radite%20i%20kvalitetnije%20uklju%C4%8Dili%20u%20procese%20dono%C5%A1enja%20odluka.%0A%C5%BDelimo%20Sabor%20koji%20je%20otvoren%20gra%C4%91anskim%20inicijativama%2C%20suradljiv%20i%20odgovoran%20prema%20svojoj%20predstavni%C4%8Dkoj%20funkciji.%20%0AImamo%20pravo%20znati%20i%20pratiti%20koliko%20odgovorno%20obavljate%20svoje%20javne%20du%C5%BEnosti%2C%20s%20kime%20se%20sastajete%20i%20savjetujete%20prilikom%20dono%C5%A1enja%20odluka.%20Tra%C5%BEimo%20da%20osigurate%20nesmetan%20rad%20neovisnih%20institucija%20i%20osna%C5%BEite%20ih%20u%20cilju%20za%C5%A1titite%20ljudskih%20prava%20i%20gra%C4%91anskih%20sloboda%20ali%20i%20prava%20na%20slobodan%20pristup%20informacijama%20i%20preispitivanje%20odluka%20i%20postupaka%20izabranih%20vlasti.%0ALjubazno%20Vas%20molimo%20da%20u%C4%8Dinite%20koliko%20je%20u%20Va%C5%A1oj%20mo%C4%87i%20da%20vratite%20povjerenje%20gra%C4%91ana%20u%20temeljne%20demokratske%20institucije%3A%0A%0A-%20maknite%20barikade%20s%20Markova%20trga%0A-%20po%C5%A1tujte%20gra%C4%91anke%20i%20gra%C4%91ane%20kojima%20slu%C5%BEite%20tako%20da%20od%20njih%20ne%20skrivate%20%C5%A1to%20radite%0A-%20po%C5%A1tujte%20funkciju%20za%20koju%20ste%20izabrani%20time%20%C5%A1to%20%C4%87ete%20otvoreno%20izlo%C5%BEiti%20svoju%20imovinu%2C%20osobne%20interese%20i%20svoj%20rad%20javnosti%2C%20te%20prijaviti%20i%20objaviti%20svaki%20dar%20i%20svaki%20sastanak%20s%20lobistima%0A-%20po%C5%A1tujte%20novinarke%20i%20novinare%20i%20vratite%20redovne%20konferencije%20na%20kojima%20vam%20mogu%20postavljati%20pitanja%20od%20javnog%20interesa%0A-%20otvorite%20zatvorene%20sjednice%20Vlade%20ili%20bar%20jasno%20propi%C5%A1ete%2C%20a%20mo%C5%BEda%20se%20i%20savjetujete%20s%20javno%C5%A1%C4%87u%20o%20tome%20koje%20vrste%20odluka%20se%20raspravljaju%20zatvoreno%20od%20javnosti%0A-%20otvorite%20javne%20rasprave%20o%20hrvatskim%20stajali%C5%A1tima%20u%20europskim%20politikama%2C%20i%20svakako%20da%20stajali%C5%A1ta%20prestanete%20donositi%20na%20zatvorenom%20dijelu%20sjednica%20Vlade%0A-%20osna%C5%BEite%20neovisne%20institucije%20koje%20nadziru%20va%C5%A1%20rad%20i%20prihvatite%20odgovornost%20za%20po%C5%A1tivanje%20na%C4%8Dela%20djelovanja%20o%20kr%C5%A1enju%20kojih%20bi%20moralo%20odlu%C4%8Divati%20neovisno%20tijelo%0A%0AS%20po%C5%A1tovanjem%2C%0A', '_blank')
  }
}

function hideWallsVlada(e) {
  if (!wallsFallen.value) {
    emit('hide')
    emit('hideWalls')
    setTimeout(() => {
      window.open('mailto:predsjednik@vlada.hr?subject=Otvorite%20Vladu%2C%20maknite%20barikade&body=Po%C5%A1tovani%20predsjedni%C4%8De%20Vlade%2C%20gospodine%20Plenkovi%C4%87u%2C%20%0A%0ASa%20%C5%BEeljom%20da%20se%20glas%20gra%C4%91anki%20i%20gra%C4%91ana%20%C4%8Duje%20i%20uva%C5%BEi%2C%20a%20rad%20demokratskih%20institucija%20bude%20vidljiv%2C%20transparentan%20i%20otvoren%2C%20Gong%20apelira%20da%20otvorite%20Vladu%20kako%20bi%20nas%20vi%C5%A1e%20i%20bolje%20informirali%20o%20onome%20%C5%A1to%20radite%20i%20kvalitetnije%20uklju%C4%8Dili%20u%20procese%20dono%C5%A1enja%20odluka.%0A%0APozivamo%20Vas%20da%20poduzmete%20potrebne%20mjere%20za%20uklanjanje%20barikada%20s%20Markova%20trga%2C%20novinarkama%20i%20novinarima%20koji%20prate%20rad%20Vlade%20osigurate%20profesionalne%20uvjete%20za%20rad%20kroz%20%20pravovremene%20najave%20sjednica%20Vlade%20i%20redovnih%20konferencije%20za%20novinare.%0A%0AImamo%20pravo%20znati%20i%20pratiti%20koliko%20odgovorno%20obavljate%20svoje%20javne%20du%C5%BEnosti%2C%20s%20kime%20se%20sastajete%20i%20savjetujete%20prilikom%20dono%C5%A1enja%20odluka.%20Tra%C5%BEimo%20da%20osigurate%20nesmetan%20rad%20neovisnih%20institucija%20i%20osna%C5%BEite%20ih%20u%20cilju%20za%C5%A1titite%20ljudskih%20prava%20i%20gra%C4%91anskih%20sloboda%20ali%20i%20prava%20na%20slobodan%20pristup%20informacijama%20i%20preispitivanje%20odluka%20i%20postupaka%20izabranih%20vlasti.%0ALjubazno%20Vas%20molimo%20da%20u%C4%8Dinite%20koliko%20je%20u%20Va%C5%A1oj%20mo%C4%87i%20da%20vratite%20povjerenje%20gra%C4%91ana%20u%20temeljne%20demokratske%20institucije%3A%0A%0A-%20maknite%20barikade%20s%20Markova%20trga%0A-%20po%C5%A1tujte%20gra%C4%91anke%20i%20gra%C4%91ane%20kojima%20slu%C5%BEite%20tako%20da%20od%20njih%20ne%20skrivate%20%C5%A1to%20radite%0A-%20po%C5%A1tujte%20funkciju%20za%20koju%20ste%20izabrani%20time%20%C5%A1to%20%C4%87ete%20otvoreno%20izlo%C5%BEiti%20svoju%20imovinu%2C%20osobne%20interese%20i%20svoj%20rad%20javnosti%2C%20te%20prijaviti%20i%20objaviti%20svaki%20dar%20i%20svaki%20sastanak%20s%20lobistima%0A-%20po%C5%A1tujte%20novinarke%20i%20novinare%20i%20vratite%20redovne%20konferencije%20na%20kojima%20vam%20mogu%20postavljati%20pitanja%20od%20javnog%20interesa%0A-%20otvorite%20zatvorene%20sjednice%20Vlade%20ili%20bar%20jasno%20propi%C5%A1ete%2C%20a%20mo%C5%BEda%20se%20i%20savjetujete%20s%20javno%C5%A1%C4%87u%20o%20tome%20koje%20vrste%20odluka%20se%20raspravljaju%20zatvoreno%20od%20javnosti%0A-%20otvorite%20javne%20rasprave%20o%20hrvatskim%20stajali%C5%A1tima%20u%20europskim%20politikama%2C%20i%20svakako%20da%20stajali%C5%A1ta%20prestanete%20donositi%20na%20zatvorenom%20dijelu%20sjednica%20Vlade%0A-%20osna%C5%BEite%20neovisne%20institucije%20koje%20nadziru%20va%C5%A1%20rad%20i%20prihvatite%20odgovornost%20za%20po%C5%A1tivanje%20na%C4%8Dela%20djelovanja%20o%20kr%C5%A1enju%20kojih%20bi%20moralo%20odlu%C4%8Divati%20neovisno%20tijelo%0A%0AS%20po%C5%A1tovanjem%2C%0A', '_blank')
    }, 2000)
    wallsFallen.value = true
  } else {
    window.open('mailto:predsjednik@vlada.hr?subject=Otvorite%20Vladu%2C%20maknite%20barikade&body=Po%C5%A1tovani%20predsjedni%C4%8De%20Vlade%2C%20gospodine%20Plenkovi%C4%87u%2C%20%0A%0ASa%20%C5%BEeljom%20da%20se%20glas%20gra%C4%91anki%20i%20gra%C4%91ana%20%C4%8Duje%20i%20uva%C5%BEi%2C%20a%20rad%20demokratskih%20institucija%20bude%20vidljiv%2C%20transparentan%20i%20otvoren%2C%20Gong%20apelira%20da%20otvorite%20Vladu%20kako%20bi%20nas%20vi%C5%A1e%20i%20bolje%20informirali%20o%20onome%20%C5%A1to%20radite%20i%20kvalitetnije%20uklju%C4%8Dili%20u%20procese%20dono%C5%A1enja%20odluka.%0A%0APozivamo%20Vas%20da%20poduzmete%20potrebne%20mjere%20za%20uklanjanje%20barikada%20s%20Markova%20trga%2C%20novinarkama%20i%20novinarima%20koji%20prate%20rad%20Vlade%20osigurate%20profesionalne%20uvjete%20za%20rad%20kroz%20%20pravovremene%20najave%20sjednica%20Vlade%20i%20redovnih%20konferencije%20za%20novinare.%0A%0AImamo%20pravo%20znati%20i%20pratiti%20koliko%20odgovorno%20obavljate%20svoje%20javne%20du%C5%BEnosti%2C%20s%20kime%20se%20sastajete%20i%20savjetujete%20prilikom%20dono%C5%A1enja%20odluka.%20Tra%C5%BEimo%20da%20osigurate%20nesmetan%20rad%20neovisnih%20institucija%20i%20osna%C5%BEite%20ih%20u%20cilju%20za%C5%A1titite%20ljudskih%20prava%20i%20gra%C4%91anskih%20sloboda%20ali%20i%20prava%20na%20slobodan%20pristup%20informacijama%20i%20preispitivanje%20odluka%20i%20postupaka%20izabranih%20vlasti.%0ALjubazno%20Vas%20molimo%20da%20u%C4%8Dinite%20koliko%20je%20u%20Va%C5%A1oj%20mo%C4%87i%20da%20vratite%20povjerenje%20gra%C4%91ana%20u%20temeljne%20demokratske%20institucije%3A%0A%0A-%20maknite%20barikade%20s%20Markova%20trga%0A-%20po%C5%A1tujte%20gra%C4%91anke%20i%20gra%C4%91ane%20kojima%20slu%C5%BEite%20tako%20da%20od%20njih%20ne%20skrivate%20%C5%A1to%20radite%0A-%20po%C5%A1tujte%20funkciju%20za%20koju%20ste%20izabrani%20time%20%C5%A1to%20%C4%87ete%20otvoreno%20izlo%C5%BEiti%20svoju%20imovinu%2C%20osobne%20interese%20i%20svoj%20rad%20javnosti%2C%20te%20prijaviti%20i%20objaviti%20svaki%20dar%20i%20svaki%20sastanak%20s%20lobistima%0A-%20po%C5%A1tujte%20novinarke%20i%20novinare%20i%20vratite%20redovne%20konferencije%20na%20kojima%20vam%20mogu%20postavljati%20pitanja%20od%20javnog%20interesa%0A-%20otvorite%20zatvorene%20sjednice%20Vlade%20ili%20bar%20jasno%20propi%C5%A1ete%2C%20a%20mo%C5%BEda%20se%20i%20savjetujete%20s%20javno%C5%A1%C4%87u%20o%20tome%20koje%20vrste%20odluka%20se%20raspravljaju%20zatvoreno%20od%20javnosti%0A-%20otvorite%20javne%20rasprave%20o%20hrvatskim%20stajali%C5%A1tima%20u%20europskim%20politikama%2C%20i%20svakako%20da%20stajali%C5%A1ta%20prestanete%20donositi%20na%20zatvorenom%20dijelu%20sjednica%20Vlade%0A-%20osna%C5%BEite%20neovisne%20institucije%20koje%20nadziru%20va%C5%A1%20rad%20i%20prihvatite%20odgovornost%20za%20po%C5%A1tivanje%20na%C4%8Dela%20djelovanja%20o%20kr%C5%A1enju%20kojih%20bi%20moralo%20odlu%C4%8Divati%20neovisno%20tijelo%0A%0AS%20po%C5%A1tovanjem%2C%0A', '_blank')
  }
}

</script>

<template>
  <div class="sidebar" :class="{ 'show': show }">
    <div @click="emit('hide')" class="mobile-collapse-line"><span></span></div>
    <img alt="Parlametar logo" class="parlametar-logo" src="../assets/parlametar_logo.svg" />
    <div v-if="showContentFor === 'parliament'">
      <h1>Gdje su svi</h1>
      <p>Tijekom dvije pandemijske godine Sabor nije objavljivao poimenične rezultate glasanja, niti podatke o tome dolaze li zastupnici i zastupnice na posao u Sabor, Ni danas ne znamo, koliko i kako zastupnice sudjeluju na sjednicama radnih tijela i što tamo govore. Iznimno, ako predsjednik radnog tijela odluči da će sjednicu prenositi na YouTube kanalu Sabora, i ako je dvorana opremljena za video-prijenos, to će ipak ostati zabilježeno i dostupno za pregled na YouTube kanalu Sabora.</p>
      <hr />
      <Accordion 
        :header-text="'Zašto bi nas trebale zanimati sjednice radnih tijela Sabora?'" 
        :body-text="'Na sjednicama radnih tijela provode se javna saslušanja poput onoga za predsjednika Vrhovnog suda RH, glavnu državnu odvjetnicu, ministre u Vladi i ostale funkcije koje mora potvrditi saborska većina. Dakle, to nije inkvizicija kako ju naziva premijer Plenković, već poslovnički instrument kojim Sabor vrši svoju nadzornu funkciju. Dodatno, na sjednicama radnih tijela sudjeluju vanjski članovi čije ćete mišljenje malo kada pronaći u zaključcima koje Sabor objavljuje na službenoj stranici, s obzirom kako se transkripti i cjeloviti zapisnici ne objavljuju.'"
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
      <p>Ako je vlast otvorena, građani mogu više sudjelovati u javnom životu, smanjuje se prostor za korupciju i bolje se štite prava građana. Ako je vlast otvorena, znači da građani nisu u mraku.</p>
      <hr />
      <Accordion 
        :header-text="'Znači li to da mogu na sjednicu?'" 
        :body-text="'Ne može se baš na sjednicu, ali dostupan je prijenos i snimka na službenoj stranici Vlade. O čemu će raspravljati na sjednici, Vlada nerijetko najavu pošalje sat ili dva prije početka same sjednice, a u svakom trenutku može odlučiti zatvoriti raspravu za javnost. Pored toga, baš svaku sjednicu Vlada zaključuje dijelom zatvorenim za javnost gdje onda raspravljaju o hrvatskim stajalištima kod donošenja EU politika i drugim europskim poslovima, robnim rezervama, kadroviranju, dodjeli sredstava i tome slično.'"
      ></Accordion>
      <hr />
      <Accordion 
        :header-text="'Što ako sam novinar_ka?'" 
        :body-text="'Onda dočekuješ ministre ispred Banskih dvora, tako je barem bilo dok se još moglo do Markovog trga. Uglavnom, redovne konferencije za javnost na kojima bi novinarke mogle postavljati pitanja- ne postoje. Recimo Stožer ih je imao za vrijeme trajanja epidemioloških mjera. Vlada zadnji put još kad je Ivica Račan bio premijer.'"
      ></Accordion>
      <a href="https://gong.hr/2022/03/28/gong-vladi-otvorite-markov-trg-i-svoj-rad-javnosti/" target="_blank" class="link-button">#OTVARAJ</a>
      <hr />
    </div>
    <div v-if="showContentFor === 'police'">
      <h1>Ti bi na Markov trg?</h1>
      <p>Markovim trgom ne možete prošetati duže od godinu i pol dana.</p>
      <p>Iza barikada pristup je dopušten samo ako ste najavili svoj dolazak na sastanak u Sabor ili Vladu, te je on prihvaćen. Ili ako ste najavili okupljanje.</p>
      <p>U tom slučaju, da biste zakoračile iza barikada, policija mora provjeriti vaše osobne dokumente i jeste li najavljeni. Međutim, ne vodi evidenciju o tome tko se, kada i zašto kretao štićenim Markovim trgom.</p>
      <a href="https://gong.hr/2022/05/24/vlada-dvije-godine-ne-dozvoljava-gradankama-na-markov-trg-mup-odgovara-bas-nas-briga-tko-tamo-prolazi/" target="_blank" class="link-button">#OTVARAJ</a>
    </div>
    <div v-if="showContentFor === 'church'">
      <div v-if="!otvaraj">
        <h1>Otvaraj!</h1>
        <p>Gong poziva Vladu i Sabor da razmotre naše preporuke i otvore se prema javnosti! Tražimo da se Vlada i Sabor otvore svoj rad javnosti i tako rade na izgradnji i očuvanju svog političkog integriteta kako bi vratili povjerenje građanki i građana u institucije.</p>
        <p>Vrijeme je da:</p>
        <ul>
          <li>maknete barikade s Markova trga</li>
          <li>poštujete građanke i građane kojima služite tako da od njih ne skrivate što radite</li>
          <li>poštujete funkciju za koju ste izabrani time što ćete otvoreno izložiti svoju imovinu, osobne interese i svoj rad javnosti, te prijaviti i objaviti svaki dar i svaki sastanak s lobistima</li>
          <li>poštujete novinarke i novinare i vratite redovne konferencije na kojima vam mogu postavljati pitanja od javnog interesa</li>
          <li>otvorite zatvorene sjednice Vlade ili bar jasno propišete, a možda se i savjetujete s javnošću o tome koje vrste odluka se raspravljaju zatvoreno od javnosti</li>
          <li>otvarite javne rasprave o hrvatskim stajalištima u europskim politikama, i svakako da stajališta prestanete donositi na zatvorenom dijelu sjednica Vlade</li>
          <li>osnažite neovisne institucije koje nadziru vaš rad i prihvatite odgovornost za poštivanje načela djelovanja o kršenju kojih bi moralo odlučivati neovisno tijelo</li>
        </ul>
        <p>Što vi mislite o tome?</p>
        <button @click="chooseAction(true)" class="link-button">#OTVARAJ</button>
        <button @click="chooseAction(false)">Nebitno</button>
      </div>
      <div v-else>
        <div v-if="sendMessage">
          <p>Čestitamo! Zato što ne odustajete od svojeg prava da kritički preispitujete rad demokratskih institucija, pozivate na odgovornost dužnosnika i uporno tražite da bolje služe društvu. Uključite se, pošaljite poruku Vladi i Saboru, vrijeme je da uvaže i naše mišljenje.</p>
          <button class="link-button wide" @click="hideWallsSabor">Piši Saboru</button>
          <button class="link-button wide" @click="hideWallsVlada">Piši Vladi</button>
        </div>
        <div v-else>
          <p>Žao nam je ako ste potonuli u političku apatiju ili mislite kako je život prekratak za borbu s vjetrenjačama, ali sjetite se pandemije i prijedloga o praćenju mobitela koji srećom u Saboru nije prošao. Zato, i ako vam je nebitno, pomislite na druge, jer država pripada svima nama. Uključite se, pošaljite poruku Vladi i Saboru.</p>
          <button class="link-button wide" @click="hideWallsSabor">Piši Saboru</button>
          <button class="link-button wide" @click="hideWallsVlada">Piši Vladi</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.sidebar {
  bottom: -100vh;
  position: absolute;
  z-index: 1001;
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
  font-size: 18px;
  font-family: 'Archivo', sans-serif;
  font-weight: 600;
  line-height: 20px;
  padding: 12px 0;
  width: 120px;
  display: inline-flex;
  justify-content: center;
  text-decoration: none;
  margin-bottom: 15px;
  display: inline-block;
  cursor: pointer;
}

button.link-button {
  width: 120px;
  font-size: 18px;
  line-height: 20px;
  margin-top: 0;
}

@media (min-width: 992px) {
  button,
  button.link-button {
    font-size: 24px;
    line-height: 25px;
    width: 170px;
  }
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

.parlametar-logo {
  max-width: 100px;
}

</style>
