<template>
  <div id="app">
    <div class="grid">
      <div class="info">
        <div class="info-inner">
          <h1 class="name">Colloque Tsui</h1>
          <p class="position">Web Developer</p>
        </div>
      </div>

      <div
        class="grid-item"
        :class="{featured: project.featured}"
        v-for="project in projects"
        :key="project.name"
      >
        <a :href="project.url" target="_blank" class="project">
          <div class="project-thumbnail">
            <picture>
              <source
                :srcset="`${project.desktop}.webp`"
                type="image/webp"
                media="(min-width: 768px)"
              >
              <source
                :srcset="`${project.mobile}.webp`"
                type="image/webp"
                media="(max-width: 767px)"
              >
              <source
                :srcset="`${project.desktop}.png`"
                type="image/png"
                media="(min-width: 768px)"
              >
              <source
                :srcset="`${project.mobile}.png`"
                type="image/png"
                media="(max-width: 767px)"
              >
              <img :src="`${project.desktop}.png`" :alt="project.name">
            </picture>
          </div>
          <div class="project-body">
            <img src="./assets/icons/external-link.svg" alt="Open in new tab" class="link-icon">
            <p class="project-title">{{ project.name }}</p>
          </div>
        </a>
      </div>
    </div>

    <ul class="contact-list">
      <li>
        <img src="./assets/icons/linkedin.svg" alt="LinkedIn" class="icons">
        <a href="http://hk.linkedin.com/pub/colloque-tsui/39/855/832/" target="_blank">Colloque Tsui</a>
      </li>
      <li>
        <img src="./assets/icons/twitter.svg" alt="Twitter" class="icons">
        <a href="https://twitter.com/colloquet" target="_blank">@colloquet</a>
      </li>
      <li>
        <img src="./assets/icons/github.svg" alt="GitHub" class="icons">
        <a href="https://github.com/colloquet" target="_blank">colloquet</a>
      </li>
      <li>
        <img src="./assets/icons/mail.svg" alt="Email" class="icons">
        <a href="mailto:colloquet@icloud.com?subject=Hello">colloquet@icloud.com</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      projects: [
        {
          name: 'LIHKG (Vue)',
          desktop: 'http://res.cloudinary.com/dfcdxc2e8/image/upload/v1518971760/lihkg-vue_kgecjy',
          mobile: 'http://res.cloudinary.com/dfcdxc2e8/image/upload/c_scale,w_600/v1518971760/lihkg-vue_kgecjy',
          url: 'https://lihkg.colloque.io',
          featured: true,
        },
        {
          name: 'iReserve Monitor',
          desktop: 'http://res.cloudinary.com/dfcdxc2e8/image/upload/v1518971760/ireserve-monitor_j8zhbd',
          mobile: 'http://res.cloudinary.com/dfcdxc2e8/image/upload/c_scale,w_600/v1518971760/ireserve-monitor_j8zhbd',
          url: 'https://ireserve.me/',
        },
        {
          name: 'Sterling Apparel',
          desktop: 'http://res.cloudinary.com/dfcdxc2e8/image/upload/v1518971762/sterling-apparel_ndhrxe',
          mobile: 'http://res.cloudinary.com/dfcdxc2e8/image/upload/c_scale,w_600/v1518971762/sterling-apparel_ndhrxe',
          url: 'http://www.sterlingapparel.com.hk/',
        },
        {
          name: 'BasicLaw.hk',
          desktop: 'http://res.cloudinary.com/dfcdxc2e8/image/upload/v1518971760/basiclaw_ldefc4',
          mobile: 'http://res.cloudinary.com/dfcdxc2e8/image/upload/c_scale,w_600/v1518971760/basiclaw_ldefc4',
          url: 'https://basiclaw.hk/',
        },
      ],
    };
  },
};
</script>

<style lang="scss">
*,
*:after,
*:before {
  box-sizing: border-box;
}

body {
  padding: 0;
  margin: 0;
  font-family: 'Lato', sans-serif;
  font-size: 16px;
  color: #000;
}

h1,
h2,
h3,
h4 {
  font-family: 'Montserrat', sans-serif;
}

.name,
.description {
  margin: 0;
}

.name {
  font-family: 'Permanent Marker', cursive;
}

a {
  text-decoration: none;
  color: #3498db;

  &:hover {
    text-decoration: underline;
    color: #2980b9;
  }

  &:visited {
    color: #9b59b6;
  }
}

img {
  max-width: 100%;
  height: auto;
  vertical-align: middle;
}

.info {
  position: relative;
  padding-left: 15px;
  width: 100%;
  text-align: center;

  &:before {
    content: '';
    display: none;
  }
}

.info-inner {
  position: relative;
  display: flex;
  justify-content: center;
  flex-direction: column;
  padding: 15px;
}

.position {
  font-weight: lighter;
  font-size: 80%;
  color: #999;
}

.grid {
  padding: 0 15px;
  margin-left: -15px;
}

.grid-item {
  float: left;
  padding-left: 15px;
  width: 100%;
  margin-bottom: 15px;
}

.project {
  position: relative;
  display: block;
  border-radius: 4px;
  box-shadow: 0 15px 35px rgba(50, 50, 93, 0.1), 0 5px 15px rgba(0, 0, 0, 0.07);
  height: 100%;
  color: #222;
  text-decoration: none;
  overflow: hidden;
  transition-property: box-shadow, transform;
  transition-duration: 0.15s;

  &:hover,
  &:visited {
    color: #222;
    text-decoration: none;
  }

  &:hover .link-icon {
    opacity: 1;
  }

  img {
    transition: transform 0.3s ease;
  }
}

.project-thumbnail {
  position: relative;
  background: #f5f5f5;
  padding-bottom: 66.66666666667%;

  img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
}

.project-body {
  position: absolute;
  background: #fff;
  padding: 10px;
  right: 0;
  bottom: 0;
  left: 0;

  *:last-child {
    margin-bottom: 0;
  }
}

.link-icon {
  position: absolute;
  width: 15px;
  top: 50%;
  right: 10px;
  opacity: 1;
  transform: translateY(-50%);
  transition: opacity 0.15s;
}

.project-title {
  margin-top: 0;
}

.contact-list {
  float: left;
  list-style: none;
  padding: 16px;
  margin: 0 0 16px;

  li {
    &:not(:first-child) {
      margin-top: 8px;
    }
  }
}

.icons {
  margin-right: 8px;
  width: 18px;
  vertical-align: bottom;
}

@media (min-width: 375px) {
  .grid-item {
    width: 50%;
  }

  .grid-item.featured {
    width: 100%;
  }
}

@media (min-width: 768px) {
  body {
    font-size: 18px;
  }

  .info {
    float: left;
    padding-left: 0;
    width: 33.33333333333%;

    &:before {
      display: block;
      padding-bottom: 66.66666666667%;
    }
  }

  .info-inner {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
  }

  .grid {
    margin: 0;
    padding: 0;
  }

  .grid-item {
    padding-left: 0;
    width: 33.33333333333%;
    margin-bottom: 0;

    &.featured {
      float: right;
      width: 66.66666666667%;
    }
  }

  .project {
    border-radius: 0;
    box-shadow: none;

    &:hover img {
      transform: scale(1.02);
    }
  }

  .project-body {
    display: none;
  }

  .link-icon {
    width: 20px;
    right: 15px;
    opacity: 0;
  }
}
</style>
