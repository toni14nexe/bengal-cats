<script setup></script>

<template>
  <main style="max-width: 90%; margin: auto">
    <ElRow
      justify="center"
      align="middle"
      v-motion-slide-top
      :duration="1000"
      :delay="1200"
      style="margin-bottom: 100px"
    >
      <ElCol align="middle">
        <h1>Politika</h1>
      </ElCol>
      <ElCol>
        <p>House of Cheetah</p>
      </ElCol>
      <ElCol>
        <p>Radnička 22b</p>
      </ElCol>
      <ElCol>
        <p>10340 Vrbovec</p>
      </ElCol>
      <ElCol>
        <p>Hrvatska</p>
      </ElCol>
      <ElCol>
        <p>+385 91 6049 331</p>
      </ElCol>
      <ElCol>
        <p>dorothea.py@gmail.com</p>
      </ElCol>
      <ElCol>
        <h1>Odricanje od odgovornosti</h1>
      </ElCol>
      <ElCol>
        <h3>Opće napomene</h3>
      </ElCol>
      <ElCol>
        <p>
          Zaštita vaših osobnih podataka izuzetno nam je važna. Ova web stranica koristi
          <b>samo osnovne (nužne) kolačiće</b> koji su potrebni za ispravno funkcioniranje stranice.
          Ne koriste se marketinški, analitički niti kolačići trećih strana.
        </p>
      </ElCol>
      <ElCol>
        <h3>Kolačići (Cookies)</h3>
      </ElCol>
      <ElCol>
        <span>
          Kolačići su male tekstualne datoteke koje vaš preglednik pohranjuje na vaše računalo ili
          mobilni uređaj. Koristimo isključivo nužne kolačiće koji omogućuju osnovne funkcije web
          stranice, kao što su:
          <ul>
            <li>prikaz stranice na odabranom jeziku</li>
            <li>pamćenje postavki kolačića (npr. prihvaćanje samo nužnih)</li>
            <li>tehničko održavanje sesije korisnika</li>
          </ul>
          Ovi kolačići ne prikupljaju osobne podatke i ne mogu vas osobno identificirati. Možete ih
          obrisati u bilo kojem trenutku putem postavki svog preglednika.
        </span>
      </ElCol>
      <ElCol>
        <h3>Odgovornost za sadržaj</h3>
      </ElCol>
      <ElCol>
        <p>
          Sadržaji na ovoj web stranici izrađeni su s najvećom pažnjom. Ipak, ne preuzimamo
          odgovornost za točnost, potpunost i ažurnost objavljenih informacija. Kao pružatelj usluge
          odgovorni smo za vlastite sadržaje na ovim stranicama u skladu s važećim zakonima
          Republike Hrvatske. Ne preuzimamo obvezu nadziranja prenesenih ili pohranjenih informacija
          trećih osoba, niti istraživanja okolnosti koje bi upućivale na nezakonitu aktivnost. U
          slučaju saznanja o mogućim povredama zakona, sporni sadržaji bit će odmah uklonjeni.
        </p>
      </ElCol>
      <ElCol>
        <h3>Odgovornost za poveznice (linkove)</h3>
      </ElCol>
      <ElCol>
        <p>
          Ova web stranica može sadržavati poveznice na vanjske internetske stranice trećih strana,
          nad čijim sadržajem nemamo utjecaja. Stoga ne preuzimamo nikakvu odgovornost za te
          sadržaje. Za sadržaj povezanih stranica odgovoran je isključivo njihov vlasnik ili
          administrator. U trenutku postavljanja poveznice provjerena je zakonitost povezanih
          stranica; nezakoniti sadržaji tada nisu bili poznati. Ako saznamo za povrede zakona, takve
          će poveznice odmah biti uklonjene.
        </p>
      </ElCol>
      <ElCol>
        <h1>Izjava o zaštiti privatnosti</h1>
      </ElCol>
      <ElCol>
        <h3>Opće napomene</h3>
      </ElCol>
      <ElCol>
        <p>
          Zaštita vaših osobnih podataka izuzetno nam je važna. Ova web stranica ne prikuplja, ne
          pohranjuje i ne obrađuje osobne podatke posjetitelja. Ne koriste se kolačići (cookies),
          alati za praćenje (npr. Google Analytics) niti dodaci društvenih mreža.
        </p>
      </ElCol>
      <ElCol>
        <h3>Zapisi poslužitelja (server log datoteke)</h3>
      </ElCol>
      <ElCol>
        <p>
          Prilikom posjete ovoj web stranici, web poslužitelj može privremeno pohraniti tehničke
          podatke (npr. IP adresu, vrstu preglednika, datum i vrijeme pristupa). Ti se podaci
          koriste isključivo radi osiguranja ispravnog rada stranice, ne koriste se za
          identifikaciju korisnika, ne prosljeđuju se trećim stranama i automatski se brišu.
        </p>
      </ElCol>
      <ElCol>
        <h3>Kontakt putem e-pošte</h3>
      </ElCol>
      <ElCol>
        <p>
          Ako nas kontaktirate putem e-pošte, vaši će se podaci koristiti isključivo za obradu vašeg
          upita i neće se prosljeđivati trećim osobama.
        </p>
      </ElCol>
      <ElCol>
        <h3>Prava korisnika</h3>
      </ElCol>
      <ElCol>
        <p>
          U svakom trenutku imate pravo zatražiti besplatnu informaciju o eventualno pohranjenim
          osobnim podacima, njihovu svrhu i izvor, kao i pravo na ispravak ili brisanje istih. Za
          sva pitanja u vezi zaštite podataka možete nas kontaktirati putem e-pošte:
          dorothea.py@gmail.com
        </p>
      </ElCol>
    </ElRow>
  </main>
</template>

<style scoped>
p,
h1 {
  margin-bottom: 24px;
}
h1,
h3 {
  color: var(--el-color-primary);
  margin: 12px 0;
}
p,
span,
ul,
li {
  color: white;
}
</style>
