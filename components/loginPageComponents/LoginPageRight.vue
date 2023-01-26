<template>
  <div class="loginPageRight">
    <div class="loginSignupWrapper">
      <h1 class="loginHeading">
        {{ signupActive ? 'Signup for free now' : 'Login into your account' }}
      </h1>
      <input-text
        v-if="signupActive"
        v-model="user.name"
        component-name="name"
        component-placeholder="Name"
        component-id="userName"
      ></input-text>
      <input-text
        v-model="user.email"
        component-name="email"
        component-placeholder="Email"
        component-id="userEmail"
        component-type="email"
      ></input-text>
      <input-text
        v-model="user.password"
        component-name="password"
        component-placeholder="Password"
        component-id="password"
        component-type="password"
      ></input-text>
      <input-text
        v-if="signupActive"
        v-model="user.passwordConfirm"
        component-name="passwordConfirm"
        component-placeholder="Password Confirm"
        component-id="passwordConfirm"
        component-type="password"
      ></input-text>

      <span
        v-if="!signupActive"
        class="forgotPassword highlight underline"
        @click="forgotPassword"
      >
        forgot password?
      </span>

      <button class="submitBtn" @click="submit">
        {{ signupActive ? 'Signup' : 'Login' }}
      </button>
    </div>
    <span class="bottomText">
      {{ signupActive ? 'Already have an account?' : 'Create an account,' }}
      <span class="highlight underline" @click="changeSignup">
        {{ signupActive ? 'Login' : 'Signup' }}
      </span>
    </span>
  </div>
</template>

<script>
import { ref, reactive } from '@nuxtjs/composition-api'
import InputText from '@/components/coreComponents/InputText.vue'

export default {
  name: 'LoginPageRight',
  components: {
    InputText,
  },
  setup() {
    const signupActive = ref(false)
    const user = reactive({
      email: '',
      password: '',
      name: '',
      passwordConfirm: '',
    })

    function changeSignup() {
      signupActive.value = !signupActive.value

      user.email = ''
      user.name = ''
      user.password = ''
      user.passwordConfirm = ''
    }

    function submit() {
      // eslint-disable-next-line no-console
      console.log(user.name, user.email, user.password, user.passwordConfirm)
    }

    function forgotPassword() {
      // eslint-disable-next-line no-console
      console.log('forgot password')
    }

    return {
      signupActive,
      user,
      changeSignup,
      submit,
      forgotPassword,
    }
  },
}
</script>

<style lang="scss" scoped>
.loginPageRight {
  height: 100%;
  background: var(--surface1);
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}

.loginHeading {
  font-size: 1.8rem;
  color: var(--text1);
  text-align: center;
  font-weight: 400;
  margin-bottom: 3rem;
}

.submitBtn {
  width: 20rem;
  padding: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 10rem;
  margin: 4rem auto 0;
  background: var(--surface2);
  border: none;
  outline: none;
  box-shadow: 0 0.2rem 0.4rem rgba(0, 0, 0, 0.1);

  &:hover {
    cursor: pointer;
  }
}

.bottomText {
  position: absolute;
  bottom: 1rem;
  left: 50%;
  transform: translateX(-50%);
  width: max-content;
  display: block;
  font-size: 1.4rem;
}

.highlight {
  color: var(--primary-400);
  display: inline-block;
  &:hover {
    cursor: pointer;
  }
}

.underline {
  text-decoration: underline;
}

.forgotPassword {
  display: inline-block;
  margin-top: 1rem;
  font-size: 1.5rem;
  width: 100%;
  text-align: right;
}
</style>
