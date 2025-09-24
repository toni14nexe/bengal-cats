<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

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
  <main>
    <div class="contact-container scroll-fade" :ref="setSectionRefs">
      <h1>Kontakt</h1>
      <p style="font-weight: 700">Želite saznati više o našim bengalskim mačkama?</p>
      <p>
        Slobodno nas kontaktirajte – s veseljem ćemo odgovoriti na sva vaša pitanja, pomoći vam u
        odabiru i pružiti sve informacije o dostupnim mačićima.
      </p>
      <p>
        Veselimo se vašoj poruci i mogućnosti da vam pomognemo pronaći savršenog novog člana
        obitelji. 💛
      </p>
      <p>
        📞 Telefon:
        <a href="tel:+385916049331">+385 91 6049 331</a>
      </p>
      <p>
        📧 E-mail:
        <a href="mailto:dorothea.py@gmail.com">dorothea.py@gmail.com</a>
      </p>
      <p>📍 Adresa: Radnička 22b</p>
      <p>📍 Mjesto: 10340 Vrbovec</p>
      <p>📍 Država: Hrvatska</p>
      <!-- <p>
        <ElRow align="middle">
          <ElIcon :size="22">
            <FacebookIcon color="#1877F2" class="facebook-icon" />
          </ElIcon>
          <a
            href="https://www.facebook.com/share/16ruahKx2D/"
            target="_blank"
            class="facebook-link"
          >
            {{ t('aboutUs.contact.facebook') }}
          </a>
        </ElRow>
      </p> -->
    </div>
  </main>
</template>

<style scoped>
.contact-container {
  display: flex;
  flex-direction: column;
  gap: 24px;
  background-color: rgba(64, 63, 69, 0.85);
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
.facebook-link {
  margin-left: 8px;
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
a {
  color: white;
}

@media only screen and (max-width: 768px) {
  .contact-container {
    padding: 5%;
  }
}

@media only screen and (max-width: 991px) {
  .facebook-icon {
    width: 18px;
    height: 18px;
  }
  .facebook-link {
    margin-left: 4px;
  }
  h1 {
    font-size: 24px;
  }
  p {
    font-size: 14px;
  }
}
</style>
