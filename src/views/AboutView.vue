<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import PageTitle from '@/components/shared/PageTitle.vue'
import TextWithSideImage from '@/components/shared/TextWithSideImage.vue'
import Contact from '@/components/shared/Contact.vue'
import TextContainer from '@/components/shared/TextContainer.vue'

const sectionRefs = ref([])
const setSectionRefs = (el) => {
  if (el && !sectionRefs.value.includes(el)) {
    sectionRefs.value.push(el)
  }
}
const observer = new IntersectionObserver(
  (entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add('fade-in')
        observer.unobserve(entry.target)
      }
    })
  },
  { threshold: 0.1 },
)

onMounted(() => {
  sectionRefs.value.forEach((el) => {
    if (el) observer.observe(el)
  })
})

onUnmounted(() => {
  sectionRefs.value.forEach((el) => {
    if (el) observer.unobserve(el)
  })
})
</script>

<template>
  <main style="max-width: 90%; margin: auto">
    <PageTitle title="O NAMA" />

    <TextContainer
      text="House of Cheetah je registrirana uzgajivačnica bengalskih mačaka i ponosni smo članovi međunarodne felinološke organizacije FIFe (Fédération Internationale Féline), te također smo aktivni članovi:
      - SFDH – Saveza felinoloških društava Hrvatske
      - FD Zagreb – Felinološkog društva Zagreb
      "
      text2="Članstvo u ovim organizacijama potvrđuje našu predanost visokim standardima uzgoja, zdravlja i dobrobiti mačaka. Radimo u skladu s međunarodnim pravilnicima, etičkim kodeksom i uzgojnim standardima za bengalsku pasminu.
      
      Naše mačke potječu iz vrhunskih svjetskih linija, uključujući poznate i priznate uzgajivačnice Kanpur, Dazzledots i AzanaBengals. Ponosni smo što gradimo naš uzgoj na kvaliteti, zdravlju i izuzetnom standardu ovih prestižnih bloodlineova. "
      class="intro-text"
    />

    <TextWithSideImage
      title="U House of Cheetah zdravlje naših mačaka uvijek je na prvom mjestu"
      text="Svi naši rasplodni mačci i mačke koji prolaze kroz kompletno genetsko testiranje preko UC Davis laboratorija, uključujući PRA-b (Progresivna atrofija retine), PKDef (Nedostatak piruvat kinaze) i test boje."
      src="/images/about-us.jpeg"
    />

    <div class="about-us-container scroll-fade" :ref="setSectionRefs">
      <h1>Detalji čine razliku</h1>
      <p>
        Uzgoj koristimo isključivo mačke koje su N/N (normalne/negativne) na PRA-b i PKDef, a za sve
        rezultate posjedujemo službene certifikate.
      </p>
      <p>
        Naše mačke redovito obavljaju i HCM (hipertrofična kardiomiopatija) preglede te PKD
        (policistična bolest bubrega) ultrazvuke kod ovlaštenih specijalista.
      </p>
      <p>
        Svaka mačka dobiva certifikat koji potvrđuje da je zdrava i urednog nalaza u trenutku
        pregleda.
      </p>
      <p>
        Također pružamo 2-godišnje zdravstveno osiguranje/garanciju na nasljedne i urođene bolesti,
        kako bismo novim obiteljima pružili dodatnu sigurnost i mir.
      </p>
      <p>
        Svi ovi zdravstveni pregledi i standardi osiguravaju da uzgajamo snažne, zdrave i genetski
        kvalitetne bengalske mačke.
      </p>
    </div>

    <Contact style="margin-top: 100px" />
  </main>
</template>

<style scoped>
.about-us-container {
  display: flex;
  flex-direction: column;
  gap: 24px;
  background-color: rgba(64, 63, 69, 0.85);
  margin-top: 100px;
  padding: 64px;
  opacity: 0.95;
  border-radius: 8px;
}
.scroll-fade {
  opacity: 0;
  transform: translateY(50px);
  transition:
    opacity 1s ease,
    transform 1s ease;
  will-change: opacity, transform;
}
.scroll-fade.fade-in {
  opacity: 1;
  transform: translateY(0);
}
.intro-text {
  margin-bottom: 150px;
}
h1 {
  color: var(--el-color-primary);
  font-weight: 700;
  font-size: 30px;
  letter-spacing: 2px;
}
p {
  font-weight: 500;
  font-size: 18px;
  letter-spacing: 0.75px;
  color: white;
}

@media only screen and (max-width: 768px) {
  .about-us-container {
    padding: 5%;
  }
  .intro-text {
    margin-bottom: 100px;
  }
}

@media only screen and (max-width: 991px) {
  h1 {
    font-size: 24px;
  }
  p {
    font-size: 14px;
  }
}
</style>
