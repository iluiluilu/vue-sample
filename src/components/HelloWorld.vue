<template>
  <div>
    <div>
      <b-tabs content-class="mt-3">
        <b-tab title="First" active @click="tabChange('form')">
          <ValidationObserver ref="form">
            <form>
              <b-row>
                <b-col>
                  <ValidationProvider name="E-mail" rules="required|email" v-slot="{ errors }">
                    <input v-model="email" type="email">
                    <span>{{ errors[0] }}</span>
                  </ValidationProvider>
                </b-col>
              </b-row>
              <b-row>
                <b-col>
                  <ValidationProvider name="First Name" rules="required|alpha" v-slot="{ errors }">
                    <input v-model="firstName" type="text">
                    <span>{{ errors[0] }}</span>
                  </ValidationProvider>
                </b-col>
              </b-row>
              <b-row>
                <b-col>
                  <ValidationProvider name="Last Name" rules="required|alpha" v-slot="{ errors }">
                    <input v-model="lastName" type="text">
                    <span>{{ errors[0] }}</span>
                  </ValidationProvider>
                </b-col>
              </b-row>
            </form>
          </ValidationObserver>
        </b-tab>
        <b-tab title="Second" @click="tabChange('form1')">
          <ValidationObserver ref="form1">
            <form>
              <b-row>
                <b-col>
                  <ValidationProvider name="E-mail1" rules="required|email" v-slot="{ errors }">
                    <input v-model="email1" type="email">
                    <span>{{ errors[0] }}</span>
                  </ValidationProvider>
                </b-col>
              </b-row>
              <b-row>
                <b-col>
                  <ValidationProvider name="First Name1" rules="required|alpha" v-slot="{ errors }">
                    <input v-model="firstName1" type="text">
                    <span>{{ errors[0] }}</span>
                  </ValidationProvider>
                </b-col>
              </b-row>
              <b-row>
                <b-col>
                  <ValidationProvider name="Last Nam1e" rules="required|alpha" v-slot="{ errors }">
                    <input v-model="lastName1" type="text">
                    <span>{{ errors[0] }}</span>
                  </ValidationProvider>
                </b-col>
              </b-row>
            </form>
          </ValidationObserver>
        </b-tab>
      </b-tabs>
    </div>
    <div><button @click="onSubmit0">test</button></div>
  </div>

</template>

<script>
import {ValidationObserver, ValidationProvider} from "vee-validate";

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {
    ValidationObserver,
    ValidationProvider
  },
  data: () => ({
    firstName: '',
    lastName: '',
    email: '',
    firstName1: '',
    lastName1: '',
    email1: '',
    currentTab: 'form',
  }),
  methods: {
    tabChange(name) {
      this.currentTab = name;
    },
    onSubmit0() {
      this.$refs[this.currentTab].validate().then(success => {
        if (!success) {
          return;
        }
        alert('Form has been submitted!');
      });
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
