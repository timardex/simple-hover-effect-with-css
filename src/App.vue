<template>
  <div id="app">
    <h1>
      Simple hover effect with CSS
    </h1>
    <nav>
      <ul>
        <li v-for="(item, index) in list" :key="index">
          <a href="#" :class="item">{{item.replace(/-/g, ' ')}}</a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  data: () => ({
    list: [
      'from-left',
      'from-right',
      'from-left-right',
      'from-top',
      'from-bottom',
      'from-middle'
    ]
  })
}

</script>

<style lang="scss">
html, body {
  margin: 0;
  height: 100%;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
}

#app {
  padding: 1rem;
}

h1 {
  text-align: center;
  margin-top: 0;
}

nav {
  padding: 15px;
  background: #fff;
  box-shadow: 0 0 15px 4px rgba(0, 0, 0, 0.2);

  ul {
    list-style: none;
    text-align: center;
    padding: 0;
    margin: 0;

    li {
      display: block;
      margin: 15px;
    }

    a {
      display: block;
      text-decoration: none;
      text-transform: capitalize;
      padding: 6px 12px;
      margin-bottom: 0;
      font-size: 1.2em;
      background-color: #f1f1f1;
      color: #000;
      position: relative;
      overflow: hidden;
      z-index: 1;
      box-shadow: 0 8px 6px -6px rgba(0, 0, 0, 0.3);

      &:hover {
        text-decoration: none;
        color: #000;
      }

      &:before,
      &:after {
        content: '';
        z-index: -1;
        position: absolute;
        margin: auto;
        background: #ffc602;
        transition: all 0.3s ease;
      }
    }
  }
}

.from-left,
.from-right {
  &:before {
    top: 0;
    width: 0;
    height: 150%;
    transform: skew(40deg);
  }

  &:hover {
    &:before {
      width: 70%;
    }
  }
}

/* FROM LEFT */
.from-left {
  &:before {
    left: -20%;
  }
}

/* FROM RIGHT */
.from-right {
  &:before {
    right: -20%;
  }
}

/* FROM LEFT AND RIGHT */
.from-left-right {
  &:before,
  &:after {
    top: 0;
    width: 0;
    height: 150%;
    transform: skew(40deg);
  }

  &:before {
    left: -20%;
  }

  &:after {
    right: -20%;
  }

  &:hover {
    &:before,
    &:after {
      width: 75%;
    }
  }
}

.from-top,
.from-bottom {
  &:before {
    width: 100%;
    height: 0;
    left: 0;
  }

  &:hover {
    &:before {
      height: 100%;
    }
  }
}
/* FROM TOP */
.from-top {
  &:before {
    top: 0;
  }
}

/* FROM BOTTOM */
.from-bottom {
  &:before {
    bottom: 0;
  }
}

/* FROM MIDDLE */
.from-middle {
  &:before {
    left: 0;
    right: 0;
    bottom: 0;
    top: 0;
    height: 100%;
    width: 0;
  }

  &:hover {
    &:before {
      width: 100%;
    }
  }
}
</style>
