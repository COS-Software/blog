<script setup>
  import { RouterLink, RouterView } from 'vue-router'
  import PostManager from '@/content/PostManager'

  const post = PostManager.getRegisteredPost()[0]
  const number = PostManager.getRegisteredPost().length
</script>

<template>
  <header>
    <section class="header">
      <div class="logo">
        <img alt="Logo" src="@/assets/logo.svg" />
      </div>

      <nav class="menu">
        <RouterLink to="/">Início </RouterLink>
        <RouterLink to="/about">Sobre</RouterLink>
        <a href="https://www.standwithukraine.how/pt">#StandWithUkraine</a>
        <a href="https://www.facebook.com/comoeuvimpararaki" to="/about">Facebook</a>
      </nav>
    </section>

    <section v-if="post" class="last-news">
      <p><small>ÚLTIMA POSTAGEM</small></p>
      <h1>
        <a :href="post.link">
          <b>#{{number}}. {{post.title}}</b>
        </a>
      </h1>
    </section>
  </header>

  <section class="content">
    <RouterView />
  </section>

  <footer>
    <div class="logo">
      <img alt="Logo" src="@/assets/logo.svg" />
    </div>

    <h3>Dúvidas ou sugestões?</h3>
    <p>Para saber mais, dar sugustões ou doações, entre em contato</p>

    <a href="https://wa.me/5567993369450">
      <button class="contact-button">CONTATAR</button>
    </a>
  </footer>
</template>

<style scoped>
  header, footer {
    background: var(--primary-color);
    color: white;
    border-radius: 20px;
    padding: 2em;
    margin-bottom: 75px;
  }

  section.header {
    display: flex;
    align-items: center;
  }

  :is(section.header, footer) .logo {
    display: block;
    width: 250px;
    margin: 10px auto ;
  }

  :is(section.header, footer) .logo img {
    width: 100%;
  }

  section.header .menu {
    flex: 0 1 80%;
  }

  section.header .menu :is(a, span) {
    margin-inline: 15px;
  }

  section.last-news {
    padding: 70px 2em;
    width: 80%;
    margin: 20px auto;
  }

  section.last-news h1 {
    font-size: 38px;
  }

  section.content, footer {
    margin-inline: 125px;
  }

  footer {
    text-align: center;
    margin-top: 175px;
  }

  .contact-button {
    background-color: var(--tertiary-color);
    padding: 15px;
    border-radius: 10px;
    color: white;
    font-weight: bold;
    margin-top: 25px;
    font-size: 10px;
    border: 0px;
    cursor: pointer;
  }
</style>