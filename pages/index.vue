<template>
  <div class="h-screen grid grid-cols-3 divide-x">
    <div class="col-span-2 h-screen flex flex-col bg-slate-100">
      <div class="flex-1 overflow-y-auto p-8">
        <app-form-profile
          v-model:name="data.n"
          v-model:desc="data.d"
          v-model:image="data.i"
        />
        <app-form-hr />
        <app-form-social-links
          v-model:facebook="data.f"
          v-model:twitter="data.t"
          v-model:instagram="data.ig"
          v-model:github="data.gh"
          v-model:telegram="data.tg"
          v-model:linkedin="data.l"
          v-model:email="data.e"
          v-model:whatsapp="data.w"
          v-model:youtube="data.y"
        />
        <app-form-hr />
        <app-form-links v-model="data.ls" />
      </div>
      <div class="border-t bg-white flex items-center">
        <button
          @click="prefillDemoData"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Add demo data </span>
          <icon name="mdi:code-json" class="h-4 w-4" />
        </button>
        <button
          @click="publish"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Publish </span>
          <icon name="ph:paper-plane-tilt-bold" class="h-4 w-4" />
        </button>
        <a
          href="https://github.com/Thescattypotty"
          target="_blank"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Github </span>
          <icon name="mdi:github" class="h-4 w-4" />
        </a>
      </div>
    </div>
    <app-form-preview :data="data" />
  </div>
</template>

<script setup>
import { encodeData } from "../utils/transformer";
const data = ref({
  n: "",
  d: "",
  i: "",
  f: "",
  t: "",
  ig: "",
  gh: "",
  tg: "",
  l: "",
  e: "",
  w: "",
  y: "",
  ls: [],
});

const prefillDemoData = () => {
  data.value = {
    n: "Bennis Yahya",
    d: "Je suis développeur FullStack, actuellement étudiant à l'École Marocaine des Sciences de l'Ingénieur. Vous trouverez ci-dessous mes certifications ainsi que leurs liens respectifs (cliquez sur le certificat pour le voir).",
    i: "https://avatars.githubusercontent.com/u/60051143",
    f: "",
    t: "",
    ig: "",
    e: "mail@bennis-yahya@outlook.com",
    gh: "https://github.com/Thescattypotty",
    tg: "",
    w: "+212622645603",
    y: "",
    l: "https://www.linkedin.com/in/yahya-bennis-3a2ba425b/",
    ls: [
      {
        l: "My Website",
        i: "ph:globe-duotone",
        u: "https://bennis-yahya.vercel.app/",
      },
      {
        l: "React Native Certificat From Meta",
        i: "ri:reactjs-line",
        u: "https://coursera.org/share/07b5281c2ac87d49e930a3a3f21ff839",
      },
      {
        l: "Git & Github Certificat From IBM",
        i: "pajamas:github",
        u: "https://coursera.org/share/094b869c663e8d6833284870b7f8e4a9",
      },
      {
        l: "Java & Object Oriented Programming Certificat from University of Pennsylvania",
        i: "mdi:language-java",
        u: "https://coursera.org/share/1920c8115d9d10eb2631bf5e05dd1ca9",
      },
      {
        l: "React Basics Certificat From Meta",
        i: "ri:reactjs-line",
        u: "https://coursera.org/share/073384991f5c4fcce6aa084760e2b443",
      },
      {
        l: "Introduction to Containers w/ Docker, Kubernetes & OpenShift Certificat from IBM",
        i: "catppuccin:devcontainer",
        u: "https://coursera.org/share/9a822b40214234c75ea2db62238a4bc3",
      },
      {
        l: "Virtual Networks in Azure from Whizlabs",
        i: "teenyicons:azure-outline",
        u: "https://coursera.org/share/7844ec8f9cfc2b56f03ef94f5b4a58c8",
      },
      {
        l: "Python for Everybody from University of Michingan",
        i: "mdi:language-python",
        u: "https://coursera.org/share/66dd07962f70ecc0dbbb7ebe5c446a7f",
      },
      {
        l: "Software Engineering: Modeling Software Systems using UML from The Hong Kong University of Science and Technology",
        i: "simple-icons:uml",
        u: "https://coursera.org/share/f7ad2b0236d5e60a7488b881f34b34c7",
      },
      {
        l: "Unix System Basics from Codio",
        i: "logos:linux-tux",
        u: "https://coursera.org/share/b123dedaec78f8f5d8dcb6085b058dc5",
      },
      {
        l: "Introduction to Cybersecurity Tools & Cyberattacks from Codio",
        i: "simple-icons:cyberdefenders",
        u: "https://coursera.org/share/b123dedaec78f8f5d8dcb6085b058dc5",
      },

    ],
  };
};

const publish = () => {
  const url = `${window.location.origin}/1?data=${encodeData(data.value)}`;
  navigator.clipboard.writeText(url).then(() => {
    alert("Link copied to clipboard");
  });
};
</script>
