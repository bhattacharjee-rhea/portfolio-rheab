---
layout: doc
---

<script setup>
  import {data as project} from './project/project.data';
  import { withBase } from 'vitepress';
</script>

# Project Phases

<ul v-if="project.length > 0">
  <li v-for="phase of project">
    <a :href="withBase(phase.url)">{{ phase.frontmatter.title }}</a>
  </li>
</ul>
<p v-else>
  Nothing here yet!
</p>