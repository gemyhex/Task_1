<template>
  <div class="container-fluid login-wrapper">
    <div class="heading-wrap">
      <div class="row">
        <div class="col-lg-12 page-head">
          <div class="overlay">
            <div class="cont">
              <nav aria-label="breadcrumb">
                <ol class="breadcrumb">
                  <li class="breadcrumb-item">
                    <router-link to="/" @click="window.location.reload()"
                      >Home</router-link
                    >
                  </li>
                  <li class="breadcrumb-item active" aria-current="page">
                    Login
                  </li>
                </ol>
              </nav>
              <h2>My Account <span>.</span></h2>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="cont offset-md-5">
      <button id="btn_show" @click="showLogin">Login</button>
      <button id="btn_show" @click="showRegister">Register</button>
    </div>

    <div class="login-wrap pt-5" v-if="reqPage === 'loginReq'">
      <div class="container">
        <div class="row">
          <div class="col-lg-5 m-auto l-side pt-5">
            <h5>
              <strong>Membership</strong>
            </h5>
            <span id="exist" v-if="infoCorrect">Account not Found</span>
            <span id="exist" v-if="passCorrect">Password incorrect</span>
            <form @submit.prevent="loginUser()" class="mt-5" novalidate>
              <label for="email">Email</label>
              <input
                v-model="user.name"
                type="text"
                name="email"
                id="email-field"
                required
              />
              <label for="password">Password</label>
              <input
                v-model="user.password"
                type="password"
                name="password"
                id="password-field"
                required
              />

              <button class="mt-4">Login</button>
              <div class="rem_lost">
                <input type="checkbox" name="remember" id="remember" />
                <label for="remember">Remember me</label>
              </div>
              <a href="#" id="lost_pass"> Lost your Password? </a>
            </form>
          </div>
        </div>
      </div>
    </div>

    <div class="register-wrapper" v-if="reqPage === 'registerReq'">
      <div class="register-wrap pt-5">
        <div class="container">
          <div class="row">
            <div class="col-lg-5 m-auto l-side pt-5">
              <h5>
                <strong>Membership</strong>
              </h5>
              <span id="exist" v-if="accExist"
                >There's Account With This Username Or Email</span
              >
              <form @submit.prevent="registerUser()" class="mt-5">
                <label for="username">Username</label>
                <input
                  v-model="user.name"
                  type="text"
                  name="username"
                  id="username-field"
                  required
                />
                <label for="password">Password</label>
                <input
                  v-model="user.password"
                  type="password"
                  name="password"
                  id="password-field"
                  required
                />
                <label for="email">User Email</label>
                <input
                  v-model="user.email"
                  type="text"
                  name="email"
                  id="email-field"
                  required
                />

                <button class="mt-4">Submit</button>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.cont {
  width: fit-content;
  height: fit-content;

  #btn_show {
    background: red;
    color: white;
    text-transform: uppercase;
    font-weight: 600;
    border: 0;
    padding: 10px 15px;
    margin: 5px 20px;
  }
}
.login-wrapper {
  .page-head {
    position: relative;
    padding: 0;
    height: 300px;
    background: rgb(49, 49, 49);
    .breadcrumb {
      background: transparent;
      li {
        a {
          color: white;
          font-weight: bold;
        }
      }
    }
    .overlay {
      .cont {
        position: absolute;
        bottom: 40%;
        left: 15%;
        color: #fff;
        h2 {
          font-size: 3rem;
          font-weight: bolder;
          span {
            color: red;
          }
        }
        p {
          font-weight: bold;
        }
      }
    }
  }

  .login-wrap {
    height: 600px;
    .container {
      height: 100%;
      .row {
        height: 100%;
      }
    }
    h5 {
      font-size: 2rem;
      font-weight: 600;
    }
    p {
      a {
        color: #000;
        font-weight: 600;
      }
    }
    .l-side {
      height: fit-content;
      label {
        display: block;
        font-weight: bold;
        margin-top: 15px;
      }
      input {
        width: 100%;
        height: 70px;
        padding: 8px 15px;
        font-weight: bold;
      }
      button {
        width: 100%;
        height: 60px;
        font-weight: bold;
        color: #fff;
        background: red;
        border: none;
      }
      .rem_lost {
        display: block;
        input {
          width: 18px;
          height: 18px;
          float: left;
          border: none;
          background: #a8a8a8;
          margin-right: 5px;
        }
        label {
          padding-left: 10px;
        }
      }
      #lost_pass {
        color: #000;
        font-weight: bold;
      }
    }
    .r-side {
      height: fit-content;
    }
  }
}

.register-wrapper {
  .page-head {
    position: relative;
    padding: 0;
    height: 300px;
    background: rgb(49, 49, 49);
    .breadcrumb {
      background: transparent;
      li {
        a {
          color: white;
          font-weight: bold;
        }
      }
    }
    .overlay {
      .cont {
        position: absolute;
        bottom: 40%;
        left: 15%;
        color: #fff;
        h2 {
          font-size: 3rem;
          font-weight: bolder;
          span {
            color: red;
          }
        }
        p {
          font-weight: bold;
        }
      }
    }
  }

  .register-wrap {
    height: 600px;
    .container {
      padding-bottom: 80px;
    }
    h5 {
      font-size: 2rem;
      font-weight: 600;
    }
    p {
      a {
        color: #000;
        font-weight: 600;
      }
    }
    .l-side {
      height: fit-content;
      label {
        display: block;
        font-weight: bold;
        margin-top: 15px;
      }
      input {
        width: 100%;
        height: 70px;
        padding: 8px 15px;
        font-weight: bold;
      }
      button {
        width: 100%;
        height: 60px;
        font-weight: bold;
        color: #fff;
        background: red;
        border: none;
      }
      .rem_lost {
        display: block;
        input {
          width: 18px;
          height: 18px;
          float: left;
          border: none;
          background: #a8a8a8;
          margin-right: 5px;
        }
        label {
          padding-left: 10px;
        }
      }
      #lost_pass {
        color: #000;
        font-weight: bold;
      }
    }
    .r-side {
      height: fit-content;
    }
  }
}
</style>

<script>
export default {
  data() {
    return {
      reqPage: "",
      accExist: false,
      infoCorrect: false,
      passCorrect: false,
      users: [],
      user: {
        name: "",
        password: "",
      },
    };
  },
  methods: {
    showLogin() {
      this.reqPage = "loginReq";
    },
    showRegister() {
      this.reqPage = "registerReq";
    },
    loginUser() {
      for (let i = 0; i < this.users.length; i++) {
        if (
          this.user.name === this.users[i].username ||
          (this.user.email === this.users[i].email &&
            this.user.password === this.users[i].password)
        ) {
          this.$store.state.userAuthorized = true;
          this.$router.push("/");
          this.$store.state.userLogin = this.user.name;
          this.$store.state.userAuthorized = true;
        } else if (
          this.user.email != this.users[i].email ||
          this.user.name != this.users[i].username
        ) {
          this.infoCorrect = true;
        } else {
          this.passCorrect = true;
        }
      }
    },
    registerUser() {
      for (let i = 0; i < this.users.length; i++) {
        if (
          this.user.name === this.users[i].username ||
          this.user.email === this.users[i].email
        ) {
          this.accExist = true;
        } else {
          this.$store.dispatch("addUser", this.user);
          console.log(this.users.length);
          this.reqPage = "loginReq";
        }
      }
      // console.log(this.user.name);
      // console.log(this.users[0].username);
    },
  },
  created() {
    this.users = this.$store.getters.getUsers;
  },
};
</script>
