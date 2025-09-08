<template>
  <div class="py-6">
    <div class="info-project">
      <h3 class="text-xl font-bold text-[#444444]">{{ project.name }}</h3>
      <p class="mt-3 text-[#555555]">{{ project.description }}</p>

      <div class="links">
        <a
          class="group flex items-center gap-2 text-[#555555] mt-5 relative"
          v-if="project.repository"
          :href="project.repository"
          target="_blank"
        >
          <span
            class="relative after:content-[''] after:absolute after:-bottom-1 after:left-0 after:w-1/4 after:h-[2px] after:bg-[#555555] after:opacity-50 after:transition-all after:duration-300 group-hover:after:w-full group-hover:after:opacity-100"
          >
            Repositório
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
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  project: {
    type: Object,
    required: true,
    default: () => ({
      name: "",
      description: "",
      repository: "",
    }),
  },
});
</script>
