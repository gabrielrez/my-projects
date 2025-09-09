<template>
  <section data-scroll="smooth">
    <img
      class="w-max max-w-[150px] rounded-full"
      :src="image"
      :alt="`Foto de ${name}`"
    />

    <h1 class="mt-10 text-[1.75rem] sm:text-[3.5rem] font-bold text-[#444444]">
      {{ name }}
    </h1>
    <p class="mt-4 text-[1.25rem] sm:text-2xl text-[#555555]">{{ role }}</p>

    <a
      class="group w-max flex items-center gap-2 mt-8 text-[1.125rem] sm:text-xl py-1 sm:py-2 text-[#555555] relative"
      :href="ctaLink"
      target="_blank"
    >
      <span
        class="relative after:content-[''] after:absolute after:-bottom-1 after:left-0 after:w-1/4 after:h-[2px] after:bg-[#555555] after:opacity-50 after:transition-all after:duration-300 group-hover:after:w-full group-hover:after:opacity-100"
      >
        {{ ctaText }}
      </span>

      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="16"
        height="16"
        fill="currentColor"
        class="bi bi-box-arrow-up-right transform transition-transform duration-300 group-hover:translate-x-1"
        viewBox="0 0 16 16"
      >
        <path
          fill-rule="evenodd"
          d="M8.636 3.5a.5.5 0 0 0-.5-.5H1.5A1.5 1.5 0 0 0 0 4.5v10A1.5 1.5 0 0 0 1.5 16h10a1.5 1.5 0 0 0 1.5-1.5V7.864a.5.5 0 0 0-1 0V14.5a.5.5 0 0 1-.5.5h-10a.5.5 0 0 1-.5-.5v-10a.5.5 0 0 1 .5-.5h6.636a.5.5 0 0 0 .5-.5"
        />
        <path
          fill-rule="evenodd"
          d="M16 .5a.5.5 0 0 0-.5-.5h-5a.5.5 0 0 0 0 1h3.793L6.146 9.146a.5.5 0 1 0 .708.708L15 1.707V5.5a.5.5 0 0 0 1 0z"
        />
      </svg>
    </a>

    <div class="mt-10 flex gap-8 items-center">
      <a
        v-for="(link, i) in socialLinks"
        :key="i"
        :href="link.url"
        target="_blank"
        class="transform transition-transform duration-150 hover:-translate-y-1"
      >
        <img :src="link.icon" class="w-8 h-8" />
      </a>
    </div>
  </section>
</template>

<script setup>
defineProps({
  image: {
    type: String,
    default: "/profile.jpeg",
  },
  name: {
    type: String,
    default: "Gabriel Rezende",
  },
  role: {
    type: String,
    default: "Desenvolvedor de Software",
  },
  ctaText: {
    type: String,
    default: "Entrar em contato",
  },
  ctaLink: {
    type: String,
    default: "https://www.linkedin.com/in/gabrielrezcp/",
  },
  socialLinks: {
    type: Array,
    default: () => [
      { url: "https://linkedin.com", icon: "linkedin.svg" },
      { url: "https://github.com", icon: "github.svg" },
    ],
  },
});
</script>
