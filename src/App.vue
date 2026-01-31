<script setup>
import { ref, onMounted } from 'vue'

import bashImg from './assets/logos/icons8-bash-48.png'
import bootstrapImg from './assets/logos/icons8-bootstrap-50.png'
import css3Img from './assets/logos/icons8-css3-48.png'
import djangoImg from './assets/logos/icons8-django-32.png'
import gitImg from './assets/logos/icons8-git-logo-48.png'
import html5Img from './assets/logos/icons8-html-5-48.png'
import javascriptImg from './assets/logos/icons8-javascript-48.png'
import linuxImg from './assets/logos/icons8-linux-48.png'
import mysqlImg from './assets/logos/icons8-mysql-logo-48.png'
import nginxImg from './assets/logos/icons8-nginx-48.png'
import nodejsImg from './assets/logos/icons8-node-js-32.png'
import phpImg from './assets/logos/icons8-php-logo-64.png'
import postgresqlImg from './assets/logos/icons8-postgresql-100.png'
import pythonImg from './assets/logos/icons8-python-48.png'
import sqlite3Img from './assets/logos/icons8-sqlite-50.png'
import tailwindcssImg from './assets/logos/icons8-tailwindcss-48.png'
import typescriptImg from './assets/logos/icons8-typescript-48.png'
import vuejsImg from './assets/logos/icons8-vuejs-48.png'
import wordpressImg from './assets/logos/icons8-wordpress-48.png'
import dockerImg from './assets/logos/icons8-docker-logo-48.png'

const estudiante = {
  nombre: 'José Manuel',
  curso: '2ºDAW',
  correo: 'joseclases222@gmail.com',
  github: 'https://github.com/jpprguezz',
}

const tecnologias = [
  { nombre: 'bash', imagen: bashImg },
  { nombre: 'bootstrap', imagen: bootstrapImg },
  { nombre: 'css3', imagen: css3Img },
  { nombre: 'django', imagen: djangoImg },
  { nombre: 'git', imagen: gitImg },
  { nombre: 'html5', imagen: html5Img },
  { nombre: 'javascript', imagen: javascriptImg },
  { nombre: 'linux', imagen: linuxImg },
  { nombre: 'mysql', imagen: mysqlImg },
  { nombre: 'nginx', imagen: nginxImg },
  { nombre: 'nodejs', imagen: nodejsImg },
  { nombre: 'php', imagen: phpImg },
  { nombre: 'postgresql', imagen: postgresqlImg },
  { nombre: 'python', imagen: pythonImg },
  { nombre: 'sqlite3', imagen: sqlite3Img },
  { nombre: 'tailwindcss', imagen: tailwindcssImg },
  { nombre: 'typescript', imagen: typescriptImg },
  { nombre: 'vuejs', imagen: vuejsImg },
  { nombre: 'wordpress', imagen: wordpressImg },
  { nombre: 'docker', imagen: dockerImg }
]

const proyectos = [
  {
    titulo: 'Lumino',
    descripcion: 'Proyecto de Lumino hecho para la asignatura de DSW usando Django',
    enlace: 'https://github.com/jpprguezz/Lumino'
  },
  {
    titulo: 'Supertodo',
    descripcion: 'Proyecto de organización de tareas para la asignatura de DSW usando Django',
    enlace: 'https://github.com/jpprguezz/Supertodo'
  },
  {
    titulo: 'Tribu',
    descripcion: 'Pequeño proyecto en el que se construye una red social para la asignatura de DSW usando Django',
    enlace: 'https://github.com/jpprguezz/Tribu'
  }
]

const seccionActiva = ref('inicio')
const menuAbierto = ref(false)
const copied = ref(false)

const irA = (seccion) => {
  seccionActiva.value = seccion
  menuAbierto.value = false
  document.getElementById(seccion).scrollIntoView({ behavior: 'smooth' })
}

const copiarCorreo = async () => {
  await navigator.clipboard.writeText(estudiante.correo)
  copied.value = true
  setTimeout(() => {
    copied.value = false
  }, 2000)
}
</script>

<template>
  <div class="min-h-screen bg-[#ccfbf1] text-[#111827]">
    <!-- Navegación -->
    <nav class="fixed top-0 left-0 w-full bg-[#ccfbf1]/95 backdrop-blur-sm z-50 border-b border-teal-200">
      <div class="max-w-5xl mx-auto px-6 py-4 flex justify-between items-center">
        <div class="text-lg font-medium tracking-tight">
          {{ estudiante.nombre }} {{ estudiante.apellido }}
        </div>
        
        <!-- Menú desktop -->
        <div class="hidden md:flex gap-8 text-sm text-[#374151]">
          <button @click="irA('inicio')" :class="{ 'text-[#111827]': seccionActiva === 'inicio' }" class="hover:text-[#111827] transition-colors">Inicio</button>
          <button @click="irA('proyectos')" :class="{ 'text-[#111827]': seccionActiva === 'proyectos' }" class="hover:text-[#111827] transition-colors">Proyectos</button>
          <button @click="irA('tecnologias')" :class="{ 'text-[#111827]': seccionActiva === 'tecnologias' }" class="hover:text-[#111827] transition-colors">Tecnologías</button>
          <button @click="irA('contacto')" :class="{ 'text-[#111827]': seccionActiva === 'contacto' }" class="hover:text-[#111827] transition-colors">Contacto</button>
        </div>

        <!-- Menú móvil -->
        <button @click="menuAbierto = !menuAbierto" class="md:hidden p-2">
          <div class="w-6 h-0.5 bg-[#111827] mb-1.5"></div>
          <div class="w-6 h-0.5 bg-[#111827]"></div>
        </button>
      </div>
      
      <!-- Menú móvil expandido -->
      <div v-if="menuAbierto" class="md:hidden border-t border-teal-200">
        <div class="flex flex-col px-6 py-4 gap-4 text-sm">
          <button @click="irA('inicio')" class="text-left text-[#374151] hover:text-[#111827]">Inicio</button>
          <button @click="irA('proyectos')" class="text-left text-[#374151] hover:text-[#111827]">Proyectos</button>
          <button @click="irA('tecnologias')" class="text-left text-[#374151] hover:text-[#111827]">Tecnologías</button>
          <button @click="irA('contacto')" class="text-left text-[#374151] hover:text-[#111827]">Contacto</button>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section id="inicio" class="min-h-screen flex items-center pt-20">
      <div class="max-w-5xl mx-auto px-6 w-full">
        <div class="max-w-2xl">
          <h1 class="text-6xl md:text-7xl font-light leading-tight tracking-tight mb-6">
            Hola, soy<br />
            <span class="font-medium">{{ estudiante.nombre }}</span>
          </h1>
          <p class="text-xl text-[#374151] leading-relaxed mb-8">
            Estudiante de {{ estudiante.curso }} apasionado por el desarrollo web.
            Me gusta crear cosas simples y funcionales.
          </p>
          <div class="flex gap-4">
            <a :href="estudiante.github" target="_blank" class="px-6 py-3 bg-[#111827] text-white text-sm hover:bg-[#374151] transition-colors">
              GitHub
            </a>
            <button @click="copiarCorreo" class="px-6 py-3 border border-[#111827] text-sm hover:bg-[#111827] hover:text-white transition-colors">
              {{ copied ? '¡Copiado!' : 'Copiar correo' }}
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- Proyectos -->
    <section id="proyectos" class="py-32">
      <div class="max-w-5xl mx-auto px-6">
        <h2 class="text-sm font-medium text-[#374151] mb-16">PROYECTOS</h2>
        <div class="space-y-16">
          <div v-for="proyecto in proyectos" :key="proyecto.titulo" class="max-w-2xl">
            <h3 class="text-2xl font-light mb-4">{{ proyecto.titulo }}</h3>
            <p class="text-[#374151] leading-relaxed mb-6">{{ proyecto.descripcion }}</p>
            <a :href="proyecto.enlace" target="_blank" class="text-sm underline decoration-1 underline-offset-4 hover:text-[#111827] transition-colors w-fit">
              Ver proyecto →
            </a>
          </div>
        </div>
      </div>
    </section>

    <!-- Tecnologías -->
    <section id="tecnologias" class="py-32 bg-[#99f6e4]">
      <div class="max-w-5xl mx-auto px-6">
        <h2 class="text-sm font-medium text-[#374151] mb-16">TECNOLOGÍAS</h2>
<div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-8">
          <div v-for="tech in tecnologias" :key="tech.nombre" class="flex items-center justify-center p-6 bg-[#a7f3d0] rounded-xl border border-[#14b8a6] hover:border-[#0d9488] hover:shadow-lg transition-all duration-300">
            <img :src="tech.imagen" :alt="tech.nombre" class="w-12 h-12 object-contain" />
          </div>
        </div>
      </div>
    </section>

    <!-- Contacto -->
    <section id="contacto" class="py-32">
      <div class="max-w-5xl mx-auto px-6">
        <h2 class="text-sm font-medium text-[#374151] mb-16">CONTACTO</h2>
        <div class="grid md:grid-cols-2 gap-16">
          <div>
            <p class="text-3xl font-light leading-tight mb-8">
              ¿Te interesa<br />trabajar conmigo?
            </p>
            <p class="text-[#374151] leading-relaxed mb-8">
              Actualmente estoy buscando oportunidades para hacer prácticas
              o proyectos. Si te interesa mi perfil, no dudes en contactarme.
            </p>
          </div>
          <div class="flex flex-col gap-6">
            <a :href="`mailto:${estudiante.correo}`" class="text-2xl hover:text-[#111827] transition-colors border-b border-gray-300 pb-2 hover:border-[#111827]">
              {{ estudiante.correo }}
            </a>
            <a :href="estudiante.github" target="_blank" class="text-xl hover:text-[#111827] transition-colors">
              GitHub
            </a>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="py-8 border-t border-teal-200">
      <div class="max-w-5xl mx-auto px-6 flex flex-col md:flex-row justify-between items-center gap-4 text-sm text-[#374151]">
        <p>{{ estudiante.nombre }} {{ estudiante.apellido }}</p>
        <p>{{ new Date().getFullYear() }}</p>
      </div>
    </footer>
  </div>
</template>

