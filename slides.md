---
theme: seriph
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
transition: slide-left
title: Welcome to Slidev
mdc: true
---

# Docker Intro

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>


<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

# What is Docker?

<br />


<img src="/docker-logo.webp" class="backgroundImg" />

<v-click>
<div class="blue">Build Once<br />Run Anywhere</div>
</v-click>


<style>
  .backgroundImg{
    position:absolute;
    width:300px;
    top: 50%;
    right:50%;
    transform:translate(150px,-100px);
    z-index: -1;
  }
  .blue{
    position:absolute;
    right:60px;
    color :#0287d1;
    font-size:30px;
    width:260px;
    border-radius:200px;
    padding:30px;
    border :1px solid #0287d1;
  }
</style>

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>


[More](http://www.dockerinfo.net/document)

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->

---

# 虚拟机 VS docker

<style>

.vm{
    position:absolute;
    width:50%;
    top: 22%;
    left:0;
    z-index: 1;
  }
.doc{
  position:absolute;
    width:50%;
    top: 22%;
    right:0;
    z-index: 1;
}

</style>

<v-click>

<img src="/vs_vm.jpeg" class="vm" />

</v-click>

<v-click>

<img src="/vs_docker.jpeg" class="doc" />

</v-click>

---

# 核心概念  

<br/>

- Container

- Image

- Dockerfile

- Volume

- Docker Registry

- Docker Compose

- Docker Daemon，Docker Engine，Network，Docker Client ...


<v-click>

<img src="/core.png"  class="w-140 absolute right-30 top-10" />
</v-click>

<style>


.get{
  position:absolute;
    width:50%;
    top: 40%;
    right:0;
    z-index: 1;
    color:#146b8c;
    font-size:28px;
}

</style>

---
transition: slide-up
level: 2
---

# Demo1. build your own image & run


```md {all|2|4|6|8|10|12}

FROM node:16-alpine

WORKDIR /app

COPY . /app/

RUN npm install -g pnpm && pnpm i

EXPOSE 8000

CMD pnpm start

```

<br />
<v-click>

ARG BUILD_ENV

ENV BUILD_ENV ${BUILD_ENV}

</v-click>
<br />

<v-click>

docker build --build-arg BUILD_ENV=production -t imageName .


</v-click>

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# Demo2. nginx项目

<br/>


```md {all|1|3|5|7|9}
FROM nginx:1.25.2-alpine

COPY /dist /usr/share/nginx/html

COPY ./nginx.conf /etc/nginx

EXPOSE 80

CMD nginx -g "daemon off;"
```

<br />

[ryf老师带你入门](https://www.ruanyifeng.com/blog/2018/02/nginx-docker.html)



<style>
.footnotes-sep {
  @apply mt-20 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>

---
layout: image
image: /docker-compose.jpeg
class: center-img
---

# Demo3. 使用 docker compose 定义前端及后端服务


<style>
.center-img {
  height:70%!important;
  top:70px;
}

</style>

---


# DevOps  &  K8S

<br />

[<img src="/devops.webp" class="w-60 m-[auto]" />](https://www.zhihu.com/question/58702398)

<br />

[<img src="/k8s.png" class="w-60 m-[auto]" />](https://www.kubernetes.org.cn/kubernetes%e8%ae%be%e8%ae%a1%e6%9e%b6%e6%9e%84)

---

# Q & A

<img src="/dockerfile.png" class="w-200 m-[auto]" />

---

# 


<div class="w-60 relative mt-6">
  <div class="relative w-40 h-40">
    <img
      v-motion
      :initial="{ x: 800, y: -100, scale: 1.5, rotate: -50 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-square.png"
    />
    <img
      v-motion
      :initial="{ y: 500, x: -100, scale: 2 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-circle.png"
    />
    <img
      v-motion
      :initial="{ x: 600, y: 400, scale: 2, rotate: 100 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-triangle.png"
    />
  </div>

  <div
    class="text-5xl absolute top-14 left-40 text-[#2B90B6] -z-1"
    v-motion
    :initial="{ x: -80, opacity: 0}"
    :enter="{ x: 0, opacity: 1, transition: { delay: 2000, duration: 1000 } }">
    Thanks
  </div>
</div>

<!-- vue script setup scripts can be directly used in markdown, and will only affects current page -->
<script setup lang="ts">
const final = {
  x: 0,
  y: 0,
  rotate: 0,
  scale: 1,
  transition: {
    type: 'spring',
    damping: 10,
    stiffness: 20,
    mass: 2
  }
}
</script>


<div>Author:  NemoZhong 
 <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>




