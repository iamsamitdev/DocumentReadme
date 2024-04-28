### Advanced NUXT 3 with BCEL
---
### ⚡ Day 1

- [ ] Section 1: การเตรียมเครื่องมือและสภาพแวดล้อม
- [ ] Section 2: ระบบ Routing แบบ File-based routing
- [ ] Section 3: โหมดการ Render แบบต่างๆ ใน Nuxt 3
- [ ] Section 4: การวาง Layout, Components และ Pages
- [ ] Section 5: การเชื่อมโยงระหว่าง Component ด้วย Nuxt Link

##### #1 ดาวน์โหลดเอกสารประกอบการเรียนรู้
- [ ] [Advanced NUXT 3 with BCEL](bit.ly/nuxt3bcel)

##### #2 Tools & Environment Setup
- [ ] [Node JS 18.x](https://nodejs.org/en/download)
- [ ] [Visual Studio Code](https://code.visualstudio.com/download)
- [ ] [Git](https://git-scm.com/downloads)

##### #3 ตรวจสอบเวอร์ชั่นของแต่ละเครื่องมือ

\#3.1 ตรวจสอบเวอร์ชั่นของ Node JS, NPM, NPX
```bash
node -v
npm -v
npx -v
```

\#3.2 ตรวจสอบเวอร์ชั่นของ Visual Studio Code
```bash
code -v
```

\#3.3 ตรวจสอบเวอร์ชั่นของ Git
```bash
git --version
```

\#3.4 แนะนำรายชื่อส่วนเสริมของ Visual Studio Code for Vue 3
- Color Picker  by anseki
- Color Highlight by Sergii N
- AutoFileName by JerryHong
- Auto Import - ES6, TS, JSX, TSX by Sergey Korenuk
- Highlight Matching Tag by vincaslt
- Material Icon Theme by Philipp Kief
- Prettier - Code formatter by Prettier
- Rainbow Brackets by 2gua
- Thunder Client by Ranga Vadhineni
- One Dark Pro by binaryify
- Vue Language Features (Volar) by Vue
- TypeScript Vue Plugin (Volar) by Vue
- Vue VSCode Snippets by sarah.drasner
- Vue 3 Snippets by hollowtree
- Tailwind CSS IntelliSense by Tailwind Labs
- vuetify-vscode by Vuetifyjs

##### #4 สร้างโปรเจค Nuxt 3 ด้วย npx

\#4.1 สร้างโฟลเดอร์เก็บโปรเจ็กต์ "Nuxt3AvdBCEL"

```bash
mkdir Nuxt3AdvBCEL
```

Step 2: เปลี่ยน path เข้าโฟลเดอร์ Nuxt3AdvBCEL
---
cd Nuxt3AdvBCEL

Step 3: สร้างโปรเจ็กต์ใหม่ด้วย Nuxt 3
---
npx nuxi init nuxt3-demo

Step 4: เปิดเข้า VSCode
---
code nuxt3-demo -r

Step 5: ติดตั้ง Dependencies (node_module)
---
npm install

Step 6: ทดสอบรันโปรเจ็กต์ dev mode
---
npm run dev

Step 7: เรียกทดสอบโปรเจ็กต์บน brownser
---
http://localhost:3000

Step 8: ฝึกใช้คำสั่ง Nuxt CLI สร้าง page
---
npx nuxi add page index

-------------------------------------------------------
# Create Nuxt 3 Project with Tailwind CSS
-------------------------------------------------------
Step 1: สร้างโปรเจ็กต์ใหม่ด้วย Nuxt 3
---
npx nuxi init nuxt3-scalable-tailwind

Step 2: เปิดเข้า VSCode
---
code nuxt3-scalable-tailwind -r

Step 3: ติดตั้ง Dependencies (node_module)
---
npm install

Step 4: ทดสอบรันโปรเจ็กต์ dev mode
---
npm run dev

Step 5: ติดตั้ง Tailwind CSS
---
npm install -D tailwindcss postcss autoprefixer

Step 6: สร้างไฟล์ tailwind config
---
npx tailwindcss init

Step 7: Add Tailwind to your PostCSS configuration in nuxt.config.js
---
postcss: {
    plugins: {
      tailwindcss: {},
      autoprefixer: {},
    },
  },

Step 8: Configure your template paths
---
mode: 'jit',
content: [
    "./components/**/*.{js,vue,ts}",
    "./layouts/**/*.vue",
    "./pages/**/*.vue",
    "./plugins/**/*.{js,ts}",
    "./nuxt.config.{js,ts}",
    "./app.vue",
  ],

Step 9: Add the Tailwind directives to your CSS
---
สร้างไฟล์ main.css ไว้ในโฟลเดอร์ ./assets/css/tailwind.css

@tailwind base;
@tailwind components;
@tailwind utilities;

Step 10: Add the CSS file globally in file nuxt.config.js
---
css: ['~/assets/css/tailwind.css'],

ทดสอบเรียกใช้ Tailwind ที่ไฟล์ app.vue
---
<div class="flex justify-center items-center h-screen">
    <h1 class="text-3xl font-bold text-purple-600 animate-bounce">
      Hello Nuxt 3
    </h1>
</div>

รันโปรเจ็กต์ทดสอบ
---
npm run dev

Step 11: ติดตั้ง @nuxtjs/robots
---
npm install @nuxtjs/robots -D

Config nuxt.config.ts for Meta SEO Tag
---
modules: [
      [
        // Nuxt Robots
        '@nuxtjs/robots',
        {
          UserAgent: "*",
          Disallow: "",
        }
      ],
    ]

and 

app: {
        head: {
            htmlAttrs: {
                lang: 'en'
            },
            bodyAttrs: {
                class: 'demo'
            },
            charset: 'utf-8',
            titleTemplate: '%s | IT Genius Engineering',
            meta: [
                {
                    name: 'author',
                    content: 'IT Genius Engineering Ltd., Thailand'
                },
                {
                    name: 'viewport',
                    content: 'width=device-width, initial-scale=1, maximum-scale=5'
                }
            ]
        }
    },

Then test use title in app.vue
---
<script lang="ts" setup>
  useHead({
    title: 'Home',
    meta: [
      { 
        name: 'description', 
        content: 'Home Nuxt 3, IT Genius Engineering' 
      },
      {
        name: 'keywords',
        content: 'Home, Nuxt 3, Learning Nuxt 3'
      },
    ],
  })
</script>

หมายเหตุ
---
หากทดสอบ Lighthouse วัดประสิทธิภาพของเว็บตอนนี้น่าจะได้ 100/100/100/100 แล้ว

Step 12: ติดตั้ง Modules Nuxt-icon
---
npm install --save-dev nuxt-icon

จากนั้นทำการ config ที่ไฟล์ nuxt.config.ts
---
modules: [
      'nuxt-icon'
],

ทดสอบเรียกใช้ icon ที่ไฟล์ app.vue
---
<Icon name="icon-park:home-two"></Icon>

Step 13: การสร้าง Components
---
npx nuxi add component App/Header

<script lang="ts" setup></script>
<template>
  <nav class="bg-gray-900 text-white py-5 border-b border-gray-700">
    <div class="container flex flex-col sm:flex-row justify-center gap-3 sm:gap-0 sm:justify-between items-center">
      <NuxtLink to="/"
        class="text-2xl font-medium">Nuxt 3 Blog</NuxtLink>
      <ul class="nav">
        <li>
          <NuxtLink to="/">Home</NuxtLink>
        </li>
        <li>
          <NuxtLink to="/categories">Categories</NuxtLink>
        </li>
      </ul>
    </div>
  </nav>
</template>

<style>
ul.nav {
  @apply flex gap-5 items-center justify-end;
}

ul.nav>li>a {
  @apply text-gray-300 hover: text-gray-50;
}

ul.nav>li>a.router-link-active {
  @apply text-primary-400;
}
</style>

npx nuxi add component App/Footer

<script lang="ts" setup></script>

<template>
  <footer class="px-4 sm:px-0 bg-gray-800 text-white">
    <div
      class="container py-4 mx-auto flex flex-col sm:flex-row justify-between gap-2 sm:items-center"
    >
      <a href="#" class="font-semibold text-lg text-white">Nuxt Tailwind</a>
      <div class="text-sm">
        Nuxt Tailwind by
        <a
          href="#"
          class="font-semibold text-white"
        >
          IT Genius
        </a>
        . All rights reserved
      </div>
    </div>
  </footer>
</template>

<style scoped></style>


Step 14: การสร้าง Layouts
---
npx nuxi add layout default

<script lang="ts" setup></script>

<template>
  <div>

    <AppHeader />
    
    <div class="container mx-auto px-4 sm:px-0 py-4">
      <slot />
    </div>

    <AppFooter />

  </div>
</template>

<style scoped></style>

Step 15: การสร้าง Pages
---
npx nuxi add page index


<script lang="ts" setup>
  useHead({
    title: 'Home',
    meta: [
      { 
        name: 'description', 
        content: 'Home Nuxt 3, IT Genius Engineering' 
      },
      {
        name: 'keywords',
        content: 'Home, Nuxt 3, Learning Nuxt 3'
      },
    ],
  })
</script>

<template>
  <div>
    
    <section
      id="hero"
      class="bg-skin-fill sm:h-screen grid place-items-center -mt-1 sm:mt-0 hero-default"
    >
      <div
        class="container mx-auto px-4 xl:px-0 flex flex-col sm:flex-row items-center justify-between gap-6 sm:gap-20"
      >
        <div class="w-full sm:w-6/12">
          <h1 class="text-4xl sm:text-6xl font-bold xl:leading-[4rem] text-skin-base">
            Nuxt 3 Tailwind
          </h1>
          <p class="text-xl mt-4 mb-14 text-skin-muted">
            Nuxt 3 + Tailwind CSS for Starter kit
          </p>
          <div class="space-x-4">
            <button class="text-2xl text-white px-4 py-3 bg-teal-700 rounded-lg">
              Get Starte
            </button>
          </div>
        </div>
        <div class="w-full sm:w-6/12 flex justify-end p-6 sm:p-0">
          <img loading="lazy" src="~/assets/images/speaker.jpg" alt="" class="w-auto rounded-lg animate-pulse">
        </div>
      </div>
    </section>

  </div>
</template>

<style scoped>

animation: bounce 1s infinite;

@keyframes bounce {
  0%, 100% {
    transform: translateY(-5%);
    animation-timing-function: cubic-bezier(0.8, 0, 1, 1);
  }
  50% {
    transform: translateY(0);
    animation-timing-function: cubic-bezier(0, 0, 0.2, 1);
  }
}

</style>


Step 16: เรียกใช้ Layout ที่ไฟล์ app.vue
---
<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>

Step 17: สร้าง BlogGrid
---
npx nuxi add component Blog/Grid

กำหนดโค้ดดังนี้
---
<script lang="ts" setup>
defineProps<{
  title: string;
  excerpt?: string;
  image?: string;
  slug?: string;
}>();
</script>

<template>
  <div class="grid shadow-xl group overflow-hidden rounded">
    <div
      v-if="image"
      class="grid__image h-[180px] w-full relative overflow-hidden"
    >
      <img
        :src="image"
        :alt="title"
        class="absolute object-cover w-full h-full group-hover:scale-110 duration-300"
      />
    </div>
    <div class="grid__content p-5">
      <h3 class="grid__content-title text-xl font-semibold mb-2">
        {{ title }}
      </h3>
      <p
        v-if="excerpt"
        class="grid__content-excerpt mb-2 text-sm text-clip overflow-hidden ..."
      >
        {{ excerpt }}
      </p>
      <NuxtLink
        v-if="slug"
        class="blog__readmore border-b-2 border-primary-500 inline-flex items-center"
        :to="`/${slug}`"
        >Read more
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="w-4 h-4 ml-1 group-hover:ml-2 duration-200"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M4.5 12h15m0 0l-6.75-6.75M19.5 12l-6.75 6.75"
          />
        </svg>
      </NuxtLink>
    </div>
  </div>
</template>

Step 18: อัพเดทไฟล์ index.vue
---

<script lang="ts" setup>
  useHead({
    title: 'Home',
    meta: [
      { 
        name: 'description', 
        content: 'Home Nuxt 3, IT Genius Engineering' 
      },
      {
        name: 'keywords',
        content: 'Home, Nuxt 3, Learning Nuxt 3'
      },
    ],
  })
</script>

<template>
  <main>
    <section class="bg-gray-100">
        <div class="container mx-auto py-12 flex items-center flex-wrap">
          <div
            class="avatar relative h-[200px] w-[200px] rounded overflow-hidden mr-10 mb-5 sm:mb-0 shadow-xl"
          >
            <img
              src="~/assets/images/smk.jpg"
              alt="Samit Koyom"
              class="absolute w-full h-full object-cover"
            />
          </div>
          <div>
            <h1 class="text-2xl font-bold">Hi, I am Samit</h1>
            <p class="mt-3 hero__des mb-5">
              I built Nuxt 3 Blog, for Learning. <br />In my free time code something for hobby.
            </p>
            <a
              href="https://twitter.com/iamsamit"
              class="bg-sky-500 hover:bg-primary-600 py-2 px-4 rounded text-white inline-flex items-center gap-2"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="16"
                height="16"
                fill="currentColor"
                class="bi bi-twitter"
                viewBox="0 0 16 16"
              >
                <path
                  d="M5.026 15c6.038 0 9.341-5.003 9.341-9.334 0-.14 0-.282-.006-.422A6.685 6.685 0 0 0 16 3.542a6.658 6.658 0 0 1-1.889.518 3.301 3.301 0 0 0 1.447-1.817 6.533 6.533 0 0 1-2.087.793A3.286 3.286 0 0 0 7.875 6.03a9.325 9.325 0 0 1-6.767-3.429 3.289 3.289 0 0 0 1.018 4.382A3.323 3.323 0 0 1 .64 6.575v.045a3.288 3.288 0 0 0 2.632 3.218 3.203 3.203 0 0 1-.865.115 3.23 3.23 0 0 1-.614-.057 3.283 3.283 0 0 0 3.067 2.277A6.588 6.588 0 0 1 .78 13.58a6.32 6.32 0 0 1-.78-.045A9.344 9.344 0 0 0 5.026 15z"
                />
              </svg>
              Let's Connect</a
            >
          </div>
        </div>
    </section>

    <!-- Blog Section Starts -->
    <section class="container mx-auto">
      <div class="container py-10">
        <div class="grid sm:grid-cols-3 gap-10">
          <BlogGrid
            title="The Dark Truth About Baby Cereal"
            image="https://www.itgenius.co.th/sandbox_api/flutter_news_api/wp-content/uploads/2021/06/little-girl-home-with-cart-vegetables_231056-89.jpg"
            excerpt="Baby cereal was first introduced in the 1930s, which was when a monumental shift occurred away from real foods towards processed convenience foods. Previously known as pablum, mothers were advised to mix it into a bottle with breast milk for babies as young as six weeks old"
            slug="https://www.itgenius.co.th/sandbox_api/flutter_news_api/the-dark-truth-about-baby-cereal/"
          ></BlogGrid>

          <BlogGrid
            title="Best Baby Games: Birth to 18 Months"
            image="https://www.itgenius.co.th/sandbox_api/flutter_news_api/wp-content/uploads/2021/06/little-boy-plays-with-colorful-pyramid-white-background-with-space-text_208700-1860.jpeg"
            excerpt="Never Too Young for Fun</h2>\n\n\n\n<p>Something about the stuffed animal we dubbed “crinkle puppy” for its crinkly sound when squeezed left my daughter Emma, 3 months at the time, smiling each time I placed it in front of her. Maybe it was the contrasting colors that held Emma’s attention. It could have been the way I often “spoke” for the puppy, giving Emma an idea of what a real puppy would sound"
            slug="https://www.itgenius.co.th/sandbox_api/flutter_news_api/best-baby-games-birth-to-18-months/"
          ></BlogGrid>

          <BlogGrid
            title="Easy Tips for Grooming Your Newborn"
            image="https://www.itgenius.co.th/sandbox_api/flutter_news_api/wp-content/uploads/2021/06/woman-brushing-young-girl-s-hair-while-sitting-near-window-woman-combing-her-3-year-old-daughter-s-hair_73762-537.jpg"
            excerpt="Grooming a newborn can be a nerve-wracking experience, especially for first-time parents From caring for the umbilical cord to trimming tiny nails, parents have a lot to learn when it comes to keeping their little ones “baby fresh. Liz Drake, a clinical nurse specialist in the neonatal intensive care unit at CHOC Children"
            slug="https://www.itgenius.co.th/sandbox_api/flutter_news_api/easy-tips-for-grooming-your-newborn/"
          ></BlogGrid>

          <BlogGrid
            title="The Dark Truth About Baby Cereal"
            image="https://www.itgenius.co.th/sandbox_api/flutter_news_api/wp-content/uploads/2021/06/little-girl-home-with-cart-vegetables_231056-89.jpg"
            excerpt="Baby cereal was first introduced in the 1930s, which was when a monumental shift occurred away from real foods towards processed convenience foods. Previously known as pablum, mothers were advised to mix it into a bottle with breast milk for babies as young as six weeks old"
            slug="https://www.itgenius.co.th/sandbox_api/flutter_news_api/the-dark-truth-about-baby-cereal/"
          ></BlogGrid>

          <BlogGrid
            title="Best Baby Games: Birth to 18 Months"
            image="https://www.itgenius.co.th/sandbox_api/flutter_news_api/wp-content/uploads/2021/06/little-boy-plays-with-colorful-pyramid-white-background-with-space-text_208700-1860.jpeg"
            excerpt="Never Too Young for Fun</h2>\n\n\n\n<p>Something about the stuffed animal we dubbed “crinkle puppy” for its crinkly sound when squeezed left my daughter Emma, 3 months at the time, smiling each time I placed it in front of her. Maybe it was the contrasting colors that held Emma’s attention. It could have been the way I often “spoke” for the puppy, giving Emma an idea of what a real puppy would sound"
            slug="https://www.itgenius.co.th/sandbox_api/flutter_news_api/best-baby-games-birth-to-18-months/"
          ></BlogGrid>

          <BlogGrid
            title="Easy Tips for Grooming Your Newborn"
            image="https://www.itgenius.co.th/sandbox_api/flutter_news_api/wp-content/uploads/2021/06/woman-brushing-young-girl-s-hair-while-sitting-near-window-woman-combing-her-3-year-old-daughter-s-hair_73762-537.jpg"
            excerpt="Grooming a newborn can be a nerve-wracking experience, especially for first-time parents From caring for the umbilical cord to trimming tiny nails, parents have a lot to learn when it comes to keeping their little ones “baby fresh. Liz Drake, a clinical nurse specialist in the neonatal intensive care unit at CHOC Children"
            slug="https://www.itgenius.co.th/sandbox_api/flutter_news_api/easy-tips-for-grooming-your-newborn/"
          ></BlogGrid>
        </div>
      </div>
    </section>
    <!-- Blog Section Ends  -->
  </main>
</template>

<style scoped>

</style>

+++++++++++++++++++++++++++++++++
| Day 2
| Nuxt3 Tailwind CSS for scalable project
+++++++++++++++++++++++++++++++++

Step 19: สร้าง page / categories, contact
---
npx nuxi add page categories/index

เพิ่มโค้ดดังนี้
---
<script lang="ts" setup>
useHead({
  title: "Categories",
  meta: [
    {
      name: "description",
      content: "Categories",
    },
  ],
});
</script>

<template>
  <section class="py-10">
    <div class="container mx-auto">
      <div class="flex flex-wrap gap-5">

        <NuxtLink
          to="/categories/clean-code"
          class="flex items-center justify-center py-2 px-4 rounded text-white shadow-md hover:shadow-lg duration-200 text-2xl uppercase bg-blue-600">
          <span class="font-semibold">#CLEAN CODE</span>
        </NuxtLink>

        <NuxtLink
          to="/categories/clean-code"
          class="flex items-center justify-center py-2 px-4 rounded text-white shadow-md hover:shadow-lg duration-200 text-2xl uppercase bg-blue-600">
          <span class="font-semibold">#JAVASCRIPT</span>
        </NuxtLink>

        <NuxtLink
          to="/categories/clean-code"
          class="flex items-center justify-center py-2 px-4 rounded text-white shadow-md hover:shadow-lg duration-200 text-2xl uppercase bg-blue-600">
          <span class="font-semibold">#DEVOPS</span>
        </NuxtLink>

      </div>
    </div>
  </section>
</template>


npx nuxi add page contact

เพิ่มโค้ดดังนี้
---
<script lang="ts" setup></script>

<template>
  <section class="bg-gray-100">
    <div class="container mx-auto py-12 flex items-center flex-wrap">
      <h1 class="text-2xl font-bold">Contact us</h1>
      <p class="py-8">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Odit atque eos reiciendis! Deserunt facere nemo doloribus quae tempore. Itaque non possimus soluta delectus alias consectetur adipisci libero minima nam explicabo!</p>
    </div>
  </section>
</template>

<style scoped>

</style>

Step 20: สร้าง .env.example และ .env
---

.env.example
--
# Use the url without trailing slash like https://example.com
WP_URI=YOUR_WORDPRESS_WEBSITE_URL

.evn
---
WP_URI=https://www.itgenius.co.th/sandbox_api/flutter_news_api


Step 21:  config nuxt.config.ts
---
runtimeConfig: {
        public: {
            wpUri: process.env.WP_URI,
        },
},

Step 22: สร้าง post.d.ts ไฟล์ไว้ในโฟลเดอร์ types
---
// define type of post for typescript wordpress rest api
export interface Post {
    id: number;
    date: string;
    title: {
        rendered: string;
    };
    slug: string;
    excerpt: {
        rendered: string;
    };
    link: string;
    author: number;
    _embedded: any;
    content: {
        rendered: string;
    };
}

Step 23: สร้าง useWpApi.ts Composables
---
/**
 * WordPress Composables
 * A collection of composable functions for WordPress.
 */

import { Post } from '~~/types/post';

export default () => {

    const config = useRuntimeConfig();
    const WP_URL: string = config.wpUri;

    const get = async <T>(endpoint: string) => {
        return useFetch<T>(`${WP_URL}/wp-json/wp/v2/${endpoint}`);
    }

    // Get all posts
    const getPosts = async (
        category?: number,
        page: number = 1,
        perPgae: number = 20,
        fields: string = 'author,id,excerpt,title,link,slug,date',
    ) => {
        let query: string = `posts?page=${page}&per_page=${perPgae}&_embed=1`;
        if (category) {
            query += `&categories=${category}`;
        }
        return get<Post[]>(query);
    }

    // Get a single post
    const getPost = async (slug: string) => {
        return get<Post[]>(`posts?slug=${slug}&_embed=1`);
    }

    // get all categories
    const getCatgories = async (fields: string = "name,slug,count") => {
        return get<any>(`categories`);
    }

    // get a single category
    const getCategory = async (slug: string) => {
        return get<any>(`categories?slug=${slug}`);
    }

    return {
        get,
        getPosts,
        getPost,
        getCatgories,
        getCategory,
    }

}


Step 23: Read blog post from api at index.vue
---
import useWpApi from '~~/composables/useWpApi';

const { data: blogs, refresh, error } = await useWpApi().getPosts();

<BlogGrid
            v-for="blog in blogs"
            :key="blog.id"
            :title="blog.title.rendered"
            :image="blog._embedded['wp:featuredmedia'][0]?.source_url"
            :excerpt="blog.excerpt.rendered"
            :slug="blog.slug"
          ></BlogGrid>

Step 24: Read blog Detail create [slug].vue
---
<script setup lang="ts">

const params = useRoute().params;
const { data: posts } = await useWpApi().getPost(params.slug as string);
const post = posts.value?.[0];

useHead({
  title: post?.title.rendered,
  meta: [
    {
      name: "description",
      content: `${post?.excerpt.rendered}`,
    },
  ],
});

</script>

<template>
   <section class="container mx-auto py-10 sm:py-16">
        <div v-if="post" class="sm:px-20">
            <!-- Blog Title -->
            <h1 class="text-3xl font-bold mb-5 text-center leading-snug" v-html="post.title.rendered"></h1>
            <!-- Blog Meta -->
            <div class="flex mb-10 justify-center gap-5">
                <span
                >Written by:
                <span class="text-primary-500">{{
                    post._embedded["author"][0]?.name
                }}</span></span
                >

                <span
                >Published on:
                <span class="text-primary-500">{{ post.date }}</span></span
                >
            </div>
            <!-- Blog Image -->
            <div
                class="blog__image h-[250px] sm:h-[500px] w-full rounded shadow-xl relative overflow-hidden mb-12"
            >
                <img
                :src="post._embedded['wp:featuredmedia'][0]?.source_url"
                :alt="post.title.rendered"
                class="absolute w-full h-full object-cover"
                />
            </div>
            <!-- Blog Content -->
            <div class="blog__content" v-html="post.content.rendered"></div>
        </div>
    </section>
</template>

<style>
.blog__content {
  @apply sm:px-10;
}
.blog__content h1,
.blog__content h2,
.blog__content h3,
.blog__content h4,
.blog__content h5,
.blog__content h6,
.blog__content p {
  @apply my-5;
}
.blog__content h1,
.blog__content h2,
.blog__content h3,
.blog__content h4,
.blog__content h5,
.blog__content h6 {
  @apply font-bold;
}

.blog__content h1 {
  @apply text-2xl sm:text-4xl;
}

.blog__content h2 {
  @apply text-xl sm:text-3xl;
}

.blog__content h3 {
  @apply text-lg sm:text-2xl;
}

.blog__content h4 {
  @apply sm:text-xl;
}

.blog__content h5 {
  @apply text-sm sm:text-lg;
}
</style>

Step 25: เรียก api หน้า category/index.vue
---
<script lang="ts" setup>

useHead({
  title: "Categories",
  meta: [
    {
      name: "description",
      content: "Categories",
    },
  ],
});

const { data: categories } = await useWpApi().getCategories();

</script>

<template>
  <section class="py-10">
    <div class="container mx-auto">
      <div class="flex flex-wrap gap-5">

        <NuxtLink
          v-for="category in categories"
          :key="(category as any).id"
          :to="`/categories/${(category as any).slug}`"
          class="flex items-center justify-center py-2 px-4 rounded text-white shadow-md hover:shadow-lg duration-200 text-2xl uppercase bg-blue-600">
          <span class="font-semibold">#{{ (category as any).name }}</span>
        </NuxtLink>

      </div>
    </div>
  </section>
</template>


Step 26: สร้างหน้าดึง blog by category ในไฟล์ categories/[slug].vue
---
<script setup lang="ts">
    const params = useRoute().params;

    const { data: categories } = await useWpApi().getCategory(params.slug as string);

    const category = categories.value[0];

    const { data: posts, error: postsError } = await useWpApi().getPosts(
        category.id
    );

    useHead({
        title: `Archive: ${category.name}`,
        meta: [
            {
                name: "description",
                content: `Category ${params.slug}`,
            },
        ],
    });



</script>

<template>
    <section class="py-10">
        <div class="container mx-auto">
            <div class="grid sm:grid-cols-3 gap-10">
                <BlogGrid
                v-for="post in posts"
                :key="post.id"
                :title="post.title.rendered"
                :image="post._embedded['wp:featuredmedia'][0]?.source_url"
                :excerpt="post.excerpt.rendered"
                :slug="post.slug"
                ></BlogGrid>
            </div>
        </div>
    </section>
</template>


<style scoped>

</style>

Step 27: ตกแต่งสีสันความสวยงามให้ category
---
สร้างไฟล์ utils/colorGenerator.ts
---
export default function (): string {
    const colors = [
      "#FFC107",
      "#F44336",
      "#03A9F4",
      "#2196F3",
      "#4CAF50",
      "#FF9800",
      "#9C27B0",
      "#E91E63",
      "#009688",
      "#3F51B5",
      "#eab308",
      "#b91c1c",
      "#292524",
      "#0d6efd",
      "#6610f2",
      "#6f42c1",
      "#d63384",
      "#dc3545",
      "#fd7e14",
      "#ffc107",
      "#28a745",
      "#20c997",
    ];
  
    return colors[Math.floor(Math.random() * colors.length)];
}  

Step 28: กำหนดสีพื้นหลัง category
---
 <NuxtLink
          v-for="category in categories"
          :key="(category as any).id"
          :to="`/categories/${(category as any).slug}`"
          class="flex items-center justify-center py-2 px-4 rounded text-white shadow-md hover:shadow-lg duration-200 text-2xl uppercase" :style="{ backgroundColor: colorGenerator() }">
          <span class="font-semibold">#{{ (category as any).name }}</span>
        </NuxtLink>

Step 29: push code ขึ้น github
---
https://github.com/iamsamitdev/nuxt3-scalable-tailwind-class-vercel

Step 30: Deployed on vercel
---
https://vercel.com/dashboard

ตัวอย่าง workshop ที่เผยแพร่แล้ว
----
https://nuxt3-scalable-tailwind-vercel.vercel.app/


+++++++++++++++++++++++++++++++++
| Day 3
| Nuxt3 Vuetify for scalable project
+++++++++++++++++++++++++++++++++
Step 1: Create new nuxt3 project
---
npx nuxi init nuxt3-scalable-vuetify

เปิดเข้า vscode
---
code nuxt3-scalable-vuetify -r

Step 2: Install sass dependencie
---
npm install -D sass@1.56.1

Step 3: Install Vuetify 3 dependencie
---
npm install -D vuetify@3.1.2

Step 4: Install Vite Plugin Vuetify
---
npm install vite-plugin-vuetify@1.0.2

Step 5: Install Nuxt Icon
---
npm install -D nuxt-icon@0.2.10

Step 6: Install Nuxt Google Fonts
---
npm install -D @nuxtjs/google-fonts@2.0.0

Step 7: Install Nuxt Robot
---
npm install -D @nuxtjs/robots@3.0.0

Step 8: Create assets/scss/style.scss
---
@use "vuetify/styles";

Step 9: Config nuxt.config.ts
---
import vuetify from "vite-plugin-vuetify"

// https://nuxt.com/docs/api/configuration/nuxt-config
export default defineNuxtConfig({
  ssr: true,
  css: ["@/assets/scss/style.scss"],
  build: {
    transpile: ["vuetify"],
  },
  vite: {
    ssr: {
      noExternal: ["vuetify"],
    },
    define: {
      "process.env.DEBUG": false,
    },
  },
  modules: [
    "nuxt-icon",
    // [
    //   "@nuxtjs/robots",
    //   {
    //     UserAgent: "*",
    //     Disallow: "",
    //   },
    // ],

    // this adds the vuetify vite plugin
		// also produces type errors in the current beta release
    async (options, nuxt) => {
			// @ts-ignore
			nuxt.hooks.hook("vite:extendConfig", (config) => config.plugins.push(vuetify()))
		},
  ],
  app: {
    head: {
      htmlAttrs: {
        lang: 'en'
      },
      bodyAttrs: {
        class: 'demo'
      },
      charset: 'utf-8',
      titleTemplate: '%s - Nuxt 3 Vuetify',
      meta: [
        { 
          name: 'viewport', 
          content: 'width=device-width, initial-scale=1, maximum-scale=5'
        },
        {
          name: 'author',
          content: "IT Genius Engineering Ltd., Thailand"
        },
      ]
    }
  },
})

Step 10: Create components/MIcon.vue
---
<script setup>

</script>

<template>
    <div>
        <Icon v-bind="$attrs" />
    </div>
</template>

Step 11: Create helpers/customIcons.ts
---
import { h } from "vue"
import type { IconSet, IconAliases, IconProps } from "vuetify"

// Custom icon component
import MIcon from "~~/components/MIcon.vue"
/**
 * Code for the icon component looks like this 
 * 
<template>
	<div>
		<Icon v-bind="$attrs" />
	</div>
</template>
<script setup></script>
 */

/**
 * Using the Phospor pack here, but any icon name can be used.
 * All of vuetify's core icons MUST be added in the `aliases` object
 */
const aliases: IconAliases = {
  complete: "ph:check-circle",
  cancel: "ph:x-circle",
  close: "ph:x-circle",
  delete: "ph:trash",
  clear: "ph:x-circle",
  success: "ph:check-circle",
  info: "ph:info",
  warning: "ph:warning",
  error: "ph:x-circle",
  prev: "ph:caret-left",
  next: "ph:caret-right",
  checkboxOn: "ph:check-square-fill",
  checkboxOff: "ph:square",
  checkboxIndeterminate: "ph:square",
  delimiter: "ph:circle",
  sort: "ph:caret-up",
  expand: "ph:caret-down",
  menu: "heroicons:bars-2",
  subgroup: "ph:caret-down",
  dropdown: "ph:caret-down",
  radioOn: "ph:radio-button-fill",
  radioOff: "ph:circle",
  edit: "ph:pencil-simple",
  ratingEmpty: "ph:star",
  ratingFull: "ph:star-fill",
  ratingHalf: "ph:star-half-fill",
  loading: "ph:spinner",
  first: "ph:caret-double-left",
  last: "ph:caret-double-right",
  unfold: "ph:arrows-out",
  file: "ph:file",
  plus: "ph:plus",
  minus: "ph:minus",
  sortAsc: undefined,
  sortDesc: undefined,
}

const custom: IconSet = {
  component: (props: IconProps) =>
    // Return render function
    h(MIcon, {
      name: props.icon,
      tag: props.tag,
      disabled: props.disabled,
    }),
}

// export both aliases and the custom object created
export { aliases, custom }


Step 12: Create helpers/themes.ts
---
import { ThemeDefinition } from 'vuetify'

// String that represents the name of the light theme
export const LIGHT_THEME = 'lightTheme'

export const lightTheme: ThemeDefinition = {
    dark: false,
    colors: {
        background: "#FFFFFF",
		surface: "#FFFFFF",
		primary: "#4f46e5",
		secondary: "#9333ea",
		error: "#ef4444",
		info: "#3b82f6",
		success: "#22c55e",
		warning: "#f59e0b",
    },
}

// String that represents the name of the dark theme
export const DARK_THEME = 'darkTheme'

export const darkTheme: ThemeDefinition = {
    dark: true,
    colors: {
        background: "#0C111B",
        surface: "#1f2937",
        primary: "#6366f1",
        secondary: "#9333ea",
        error: "#ef4444",
        info: "#3b82f6",
        success: "#22c55e",
        warning: "#f59e0b",
    }, 
}

Step 13: Create helpers/defaults.ts
---
import { DefaultsInstance } from "vuetify/lib/framework.mjs"

export const defaults: DefaultsInstance = {
    VAppBar: {
		elevation: 0,
	},
	VBtn: {
		variant: "flat",
		height: 38,
		rounded: "lg",
		size: "small",
	},
	VTextField: {
		color: "primary",
		variant: "outlined",
		density: "comfortable",
	},
}

Step 14: Create plugins/vuetify.ts
---
// import createVuetify from "vuetify"
import { createVuetify } from "vuetify"

// import custom icons from helpers
import { aliases, custom } from "@/helpers/customIcons"

// import theme from "@/helpers/themes"
import { LIGHT_THEME, lightTheme, DARK_THEME, darkTheme } from "@/helpers/themes"

// import defaults from "@/helpers/defaults"
import { defaults } from "@/helpers/defaults"

export default defineNuxtPlugin((nuxtApp ) => {
    // Create a new Vuetify instance
    const vuetify = createVuetify({
        ssr: true,
        defaults,
        theme: {
            defaultTheme: LIGHT_THEME,
            themes: {
                lightTheme,
                darkTheme,
            },
            // add color variations
            variations: {
                colors: ["primary", "secondary"],
                lighten: 3,
                darken: 3,
            }
        },
        // Add the custom iconset
        icons: {
            defaultSet: "custom",
            aliases,
            sets: {
                custom,
            },
        },
    })

    // Inject it to nuxtApp
    nuxtApp.vueApp.use(vuetify)
})

Step 15: Update app.vue
---
<template>
  <div>
    <v-card class="mx-auto" width="400">
      <v-card-title>
        Card Title
      </v-card-title>
      <v-card-text>
        This is content
      </v-card-text>
      <v-card-actions>
        <v-btn variant="text" color="teal-accent-4">
          Learn More
        </v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

Step 16: Run project in dev mode
---
npm run dev

Step 17: Create layouts/default.vue
---
<template>
	<div>
		<VApp>
			<VMain>
				<slot />
			</VMain>
		</VApp>
	</div>
</template>


Step 18: Create pages/index.vue for login page
----
code in example file...

Step 19: custom scss/style.scss
---
// Override the textfield's radius
.v-text-field {
	.v-field__outline__start {
		border-radius: 10px 0 0 10px !important;
	}
	.v-field__outline__end {
		border-radius: 0 10px 10px 0 !important;
	}
}

.v-btn {
	font-weight: 700 !important;
}
.label {
	font-weight: 600;
	font-size: 15px;
	margin-bottom: 6px;
	display: inline-block;
	cursor: pointer;
}
// Theme gradients
.gradient {
	&.primary {
		color: white;
		background: linear-gradient(
			318deg,
			rgba(67, 56, 202, 1) 12%,
			rgba(79, 70, 229, 1) 38%,
			rgba(99, 102, 241, 1) 100%
		) !important;
	}
	&.cancel {
		// color: #1e293b;
		background: linear-gradient(
			318deg,
			rgba(203, 213, 225, 1) 12%,
			rgba(226, 232, 240, 1) 38%,
			rgba(241, 245, 249, 1) 100%
		) !important;
	}
	&.success {
		color: white;
		background: linear-gradient(
			318deg,
			rgba(21, 128, 61, 1) 12%,
			rgba(22, 163, 74, 1) 38%,
			rgba(34, 197, 94, 1) 100%
		) !important;
	}
	&.info {
		color: white;
		background: linear-gradient(
			318deg,
			rgba(30, 64, 175, 1) 12%,
			rgba(37, 99, 235, 1) 38%,
			rgba(59, 130, 246, 1) 100%
		) !important;
	}
	&.warn {
		color: white;
		background: linear-gradient(
			318deg,
			rgba(180, 83, 9, 1) 12%,
			rgba(217, 119, 6, 1) 38%,
			rgba(245, 158, 11, 1) 100%
		) !important;
	}
	&.error {
		color: white;
		background: linear-gradient(
			318deg,
			rgba(153, 27, 27, 1) 12%,
			rgba(220, 38, 38, 1) 38%,
			rgba(248, 113, 113, 1) 100%
		) !important;
	}
	&.gray {
		color: white;
		background: linear-gradient(
			318deg,
			rgba(30, 41, 59, 1) 12%,
			rgba(44, 55, 74, 1) 38%,
			rgba(71, 85, 105, 1) 100%
		) !important;
	}
}

// enforce font globally
*,
html,
body {
	font-family: 'Inter','IBM Plex Sans Thai', sans-serif!important;
	-webkit-font-smoothing: antialiased !important;
}
Step 20: Set fonts in nuxt.config.ts
---
link: [
        {
					rel: "stylesheet",
					href: "https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Thai:wght@200;300;400;500;600;700&family=Inter:wght@200;300;400;500;600;700;800;900&display=swap",
				},
				{ rel: "icon", type: "image/x-icon", href: "/favicon.ico" },
      ],


Step 21: Create register in pages/signup/index.vue
---
code in example file...

Step 22: Validation form create composables/useFormRules.ts
---
// Create a custom hook to use in your components
export const useFormRules = () => {
    return {
        ruleRequired: (value: string) => !!value || 'This field is required',
        ruleEmail: (value: string) => {
            const pattern =
				/^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
			return pattern.test(value) || "Enter a valid email";
        },
        rulePassLen: (v: string) => (!!v && v.length >= 6) || "Password must be 6 chars or more",
    }
}

Step 23: Create Backend Server with Strapi
---
npx create-strapi-app@latest strapi-api  --quickstart

+++++++++++++++++++++++++++++++++
| Day 4
| Nuxt 3 JWT authentication with Strapi Backend
+++++++++++++++++++++++++++++++++

Step 1: Create Backend Server with Strapi and MySQL Database
---
npx create-strapi-app@latest strapi-mysql-api

Step 2: เซ็ตไฟล์ .env
---
STRAPI_URL=http://localhost:1337/api

Step 3: เซ็ตค่า config ที่ไฟล์ nuxt.config.ts
---
// runtime config
    runtimeConfig: {
        public: {
            strapi: {
                url: process.env.STRAPI_URL || "http://localhost:1337/api",
            },
        },
    },

Step 4: เขียนส่วนการ login pages/index.vue
---


Step 5: สร้าง middleware สำหรับการ protect route
---
npx nuxi add middleware auth


+++++++++++++++++++++++++++++++++
| Day 5
| Nuxt 3 JWT with Strapi
+++++++++++++++++++++++++++++++++

Step 1: Install @faker-js/faker for fake data
---
npm install @faker-js/faker@7.6.0 -D

Step 2: แก้ไขไฟล์ strapi-mysql-api/src/index.ts
---
const { faker } = require('@faker-js/faker')

fake category
---
async bootstrap({ strapi }) {
    for (let i = 0; i < 3; i++) {
      await strapi.entityService.create("api::category.category",{
        data: {
          title: faker.word.adjective(),
          status: 1,
          publishedAt: '2023-02-11 21:33:38.928000',
          created_by_id: 1,
          updated_by_id: 1
        },
      });
    }
},

fake product
---
async bootstrap({ strapi }) {
    for (let i = 0; i < 3; i++) {
      await strapi.entityService.create("api::product.product",{
        data: {
          title: faker.word.adjective() + " " + faker.word.noun(),
          slug: faker.lorem.slug(),
          description: faker.lorem.paragraph(),
          price: faker.commerce.price(),
          qty: 5,
          is_featured: 1,
          category: 2,
          publishedAt: '2023-02-11 21:33:38.928000',
          created_by_id: 1,
          updated_by_id: 1
        },
      });
    }
},

Strapi JWT Configuration
---
https://docs.strapi.io/developer-docs/latest/plugins/users-permissions.html

create file config/plugins.ts
---
module.exports = (env) => ({
    'users-permissions': {
        enabled: true,
        config: {
        jwt: {
            expiresIn: '2d', // Default millisecond (60s)  1 minute
        },
    }
  },
})

Step 3: ติดตั้ง SweetAlert 2 สำหรับทำ popup
---
npm i sweetalert2@11.7.1 -D

Step 4: ติดตั้ง library ที่ต้องใช้สำหรับหน้า backend
---
npm i @mdi/font@7.0.96 -D
npm i apexcharts@3.35.0 -D
npm i vue3-apexcharts@1.4.1 -D

Step 5: ทำการ config file nuxt.config.ts
---
ssr: true,
routeRules: {
    '/backend/**': { ssr: false },
},

// import vuetify css
css: [
        "@/assets/scss/style.scss",
        "@/assets/backend/style.scss",
],

Step 6: สร้าง Layout สำหรับ backend
----


Step 7: สร้าง types สำหรับ products
---
types/product.d.ts


Step 8: สร้าง composable สำหรับอ่านข้อมูลจาก strapi api
---
composables/useStrapiApi.ts

+++++++++++++++++++++++++++++++++
| เก็บตกตอนที่ 1
| Nuxt 3 Pagination with Vuetify 3
+++++++++++++++++++++++++++++++++
Step 1: ทำการแสดงตัว Pagination ของ Vuetify
---
https://vuetifyjs.com/en/components/paginations/

Step 2: ปรับ API ของ Strapi
---
https://docs.strapi.io/dev-docs/api/rest/sort-pagination

Step 3: อัพเดทตัว Service ที่เรียก API
----

// config
    const config = useRuntimeConfig()
    const STRAPI_URL: string = config.strapi.url

    // get token from cookie
    const token = useCookie('token')

    // headers
    const headers = {
        'Content-Type': 'application/json',
        "Authorization": `Bearer ${token.value}`
    }

    // Get All Products
    const getProducts = async (page: number, pagesize: number) => {
        return useFetch<ProductResponse & MetaResponse>(`${STRAPI_URL}/products?sort[0]=id%3Adesc&pagination[page]=${page}&pagination[pageSize]=${pagesize}&populate=*`, {
            method: 'GET',
            headers: headers,
            cache: 'no-cache',
        })
    }



+++++++++++++++++++++++++++++++++
| เก็บตกตอนที่ 2
| Nuxt 3 Pinia
+++++++++++++++++++++++++++++++++
Step 3: Install Pinia for state management
---
https://pinia.vuejs.org/ssr/nuxt.html

npm install pinia -D --legacy-peer-deps
npm install @pinia/nuxt -D --legacy-peer-deps

Step 4: Config pinia in nuxt.config.ts file
---
// nuxt.config.js
export default defineNuxtConfig({
  // ... other options
  modules: [
    // ...
    '@pinia/nuxt',
  ],
})

Step 5: Create stores/counter.ts
---
// stores/counter.js
import { defineStore } from 'pinia'

export const useCounterStore = defineStore('counter', {
  state: () => {
    return { count: 0 }
  },
  // could also be defined as
  // state: () => ({ count: 0 })
  actions: {
    increment() {
      this.count++
    },
    decrement() {
      this.count--
    }
  },
})


Step 6: Test use CounterStore in pages/counter/index.vue
---

<script setup lang="ts">
    
    // import store counter
    import { useCounterStore } from '@/stores/counter'

    // create counter object
    const counter = useCounterStore()

</script>

<template>
  <div>
    <v-card class="mx-auto" width="400">
      <v-card-title>
        Counter
      </v-card-title>
      <v-card-text>
        <p>Count: {{ counter.count }}</p>
      </v-card-text>
      <v-card-actions>
        <v-btn variant="text" color="teal-accent-4" @click="counter.increment()">
            Count Up
        </v-btn>
        <v-btn variant="text" color="red-accent-4" @click="counter.decrement()">
            Count Down
        </v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<style scoped>

</style>