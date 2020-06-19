<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated>
      <q-toolbar>
        <q-icon name="people_alt" size="md" />
        <q-toolbar-title> OneWork &middot; <b>Sign in</b> </q-toolbar-title>
      </q-toolbar>
    </q-header>
    <q-page-container>
      <q-page padding>
        <q-card>
          <q-tabs
            v-model="activeTab"
            dense
            class="text-grey"
            active-color="primary"
            indicator-color="primary"
            align="justify"
            narrow-indicator
          >
            <q-tab name="login" label="Login" />
            <q-tab name="forgotPassword" label="Forgot Password" />
            <q-tab name="register" label="Register" />
          </q-tabs>

          <q-separator />

          <q-tab-panels v-model="activeTab" animated>
            <q-tab-panel name="login" class="q-gutter-sm">
              <div class="text-h6">Login user</div>
              <q-banner class="bg-grey-3">
                <template v-slot:avatar>
                  <q-icon name="account_circle" color="primary" />
                </template>
                Welcome to OneWork. Please enter your credentials to log in.
              </q-banner>
              <q-input outlined v-model="login.username" label="Username" />
              <q-input
                outlined
                v-model="login.organization"
                label="Organization"
              />
              <div class="text-right">
                <a class="text-primary link" @click="setActiveTab('register')">
                  Not yet registered?
                </a>
              </div>
              <q-input
                type="password"
                outlined
                v-model="password"
                label="Password"
              />
              <div class="text-right">
                <a
                  class="text-primary link float-right"
                  @click="setActiveTab('forgotPassword')"
                >
                  Forgotten your password?
                </a>
              </div>
              <q-checkbox v-model="login.remember">
                Remember login
              </q-checkbox>
              <div class="row">
                <q-space />
                <q-btn color="primary" label="Log in" />
              </div>
            </q-tab-panel>

            <q-tab-panel name="forgotPassword" class="q-gutter-sm">
              <div class="text-h6">Forgot password</div>
              <q-banner class="bg-grey-3">
                <template v-slot:avatar>
                  <q-icon name="lock_open" color="primary" />
                </template>
                If forgotten your password then reset it by following the
                instructions that will be sent to you by email.
              </q-banner>
              <q-input outlined v-model="username" label="Username" />
              <q-input outlined v-model="organization" label="Organization" />
              <div class="row">
                <q-space />
                <q-btn color="primary" label="Reset password" />
              </div>
            </q-tab-panel>

            <q-tab-panel name="register" class="q-gutter-sm">
              <div class="text-h6">Register organization</div>
              <q-banner class="bg-grey-3">
                <template v-slot:avatar>
                  <q-icon name="domain" color="primary" />
                </template>
                Please register your organization if not already done. Otherwise
                go to the
                <a
                  @click.prevent="setActiveTab('login')"
                  class="text-primary link"
                >
                  Login Page
                </a>
              </q-banner>
              <div class="text-h7">Organization</div>
              <q-input outlined v-model="register.organization.id" label="ID" />
              <q-input
                outlined
                v-model="register.organization.name"
                label="Organization name"
              />
              <q-input
                outlined
                v-model="register.organization.street"
                label="Street"
              />
              <div class="row">
                <q-input
                  outlined
                  v-model="register.zip"
                  label="Zip"
                  class="q-mr"
                />
                <q-input
                  outlined
                  v-model="register.organization.city"
                  label="City"
                />
              </div>
              <q-select
                outlined
                v-model="register.organization.country"
                :options="availableCountries"
                label="Country"
              />
              <q-input
                type="password"
                outlined
                v-model="password"
                label="Password"
              />

              <div class="text-h7">Admin user</div>
              <q-input
                outlined
                v-model="register.adminUser.username"
                label="Username"
              />
              <q-input
                outlined
                v-model="register.adminUser.firstName"
                label="First name"
              />
              <q-input
                outlined
                v-model="register.adminUser.lastName"
                label="Last name"
              />
              <q-input
                outlined
                v-model="register.adminUser.lastName"
                label="E-mail"
              />
              <q-input
                outlined
                v-model="register.adminUser.password"
                label="Password"
              />
              <q-input
                outlined
                v-model="register.adminUser.password2"
                label="Repeat password"
              />
              <q-checkbox v-model="register.termsAndConditions.accept">
                Accept <a class="text-primary link">Terms and Conditions</a>
              </q-checkbox>

              <div class="row">
                <q-space />
                <q-btn color="primary" label="Register and log in" />
              </div>
            </q-tab-panel>
          </q-tab-panels>
        </q-card>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">
export default {
  data() {
    return {
      activeTab: 'login',
      login: {
        username: '',
        organiazation: '',
        password: '',
        remember: false
      },
      register: {
        organization: {
          id: '',
          name: '',
          street: '',
          zip: '',
          city: '',
          country: ''
        },
        adminUser: {
          username: '',
          firstName: '',
          lastName: '',
          email: '',
          password: '',
          password2: ''
        },
        termsAndConditions: {
          accept: false
        }
      },
      forgotPassword: {
        username: ''
      },
      availableCountries: [
        { label: 'United States', value: 'US' },
        { label: 'United Kingdom', value: 'GB' },
        { label: 'Germany', value: 'DE' }
      ]
    }
  },

  methods: {
    setActiveTab(name: string) {
      this.activeTab = name
    }
  }
}
</script>

<style scoped>
.link {
  cursor: pointer;
}
</style>
