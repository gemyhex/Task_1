<template>
  <nav class="header-wrapper">
    <div class="top-nav px-5" id="topnav">
      <div class="links">
        <ul>
          <li>
            <router-link to="/" class="active">home</router-link>
          </li>
          <li>
            <router-link to="/account">account</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      clicked: false,
    };
  },
  methods: {},
};
</script>

<style lang="scss" scoped>
.header-wrapper {
  width: 100%;
  height: 60px;
  overflow: hidden;
  position: fixed;
  top: 0;
  left: 0;
  background: #3f3f3f;
  z-index: 99;
  padding: 5px 20px;
  .top-nav {
    display: flex;
    .links {
      width: fit-content;
      height: fit-content;
      text-align: center;
      padding-top: 10px;
      margin: 0 auto;
      ul {
        width: fit-content;
        margin: 0;
        li {
          display: inline-block;
          text-transform: uppercase;
          padding: 5px 15px;
          a {
            color: white;
            text-decoration: none;
            font-weight: bold;
            &:hover {
              color: rgb(233, 1, 1);
              transition: all 0.5s ease;
            }
          }
        }
      }
    }
  }
}
</style>
