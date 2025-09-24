<script setup>
import PageTitle from '@/components/shared/PageTitle.vue'
import TextWithSideImage from '@/components/shared/TextWithSideImage.vue'
import Contact from '@/components/shared/Contact.vue'
</script>

<template>
  <main style="max-width: 90%; margin: auto">
    <PageTitle title="KONTAKT" />
    <TextWithSideImage
      title="Korak bliže vašem novom prijatelju"
      text="Imate pitanja o našim bengalskim mačkama ili želite dogovoriti posjetu i upoznati ih uživo? Slobodno nas kontaktirajte putem telefona ili e-pošte. S veseljem ćemo vam pomoći pronaći mačića koji će savršeno odgovarati vašem domu i načinu života. 🐆✨"
      src="/images/contact.jpg"
    />
    <Contact style="margin-top: 100px" />
  </main>
</template>

<style scoped></style>
