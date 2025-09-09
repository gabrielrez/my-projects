<script setup>
import { ref, onMounted } from "vue";
import ProfileCard from "./components/ProfileCard.vue";
import ProjectItem from "./components/ProjectItem.vue";

const projects = ref([]);
const loading = ref(true);

const API_URL =
  "https://raw.githubusercontent.com/gabrielrez/my-projects/main/README.md";

onMounted(async () => {
  try {
    const res = await fetch(API_URL);
    const markdown = await res.text();
    const match = markdown.match(/```json([\s\S]*?)```/);

    if (match) {
      projects.value = JSON.parse(match[1].trim());
      console.log("Projetos carregados:", projects.value);
    } else {
      console.warn("Nenhum bloco JSON encontrado no README.md");
    }
  } catch (err) {
    console.error("Erro ao carregar projetos:", err);
  } finally {
    loading.value = false;
  }
});

function scrollToTop() {
  window.scrollTo({ top: 0, behavior: "smooth" });
}
</script>

<template>
  <main class="mt-10 sm:mt-20 px-5 mx-auto max-w-[600px]">
    <ProfileCard />

    <section class="projects mt-24">
      <h2 class="text-2xl font-semibold mb-8 text-[#DADADA]">
        &lt;Projetos/&gt;
      </h2>

      <p v-if="loading">Carregando projetos...</p>

      <ProjectItem
        v-for="project in projects"
        :key="project.name"
        :project="project"
        class="mb-5"
      />
    </section>

    <section class="flex justify-center mb-10">
      <a class="mt-10 p-2 text-[#444444] cursor-pointer" @click="scrollToTop"
        >Voltar ao topo ↑</a
      >
    </section>
  </main>
</template>
