<template>
  <c-page-layout>
    <template v-slot:header>
      <div class="text-h6">Employees</div>
    </template>

    <template v-slot:actions>
      <q-btn rounded flat>
        <q-icon name="search" />
      </q-btn>
      <q-btn rounded flat>
        <q-icon name="sort" />
      </q-btn>
      <q-btn rounded flat>
        <q-icon name="add" />
      </q-btn>
    </template>

    <template>
      <div class="q-mt-sm">
        <q-list>
          <div v-for="(item, index) in data" :key="item.name">
            <q-item clickable v-ripple>
              <q-item-section avatar>
                <c-avatar
                  :firstName="item.firstName"
                  :lastName="item.lastName"
                />
              </q-item-section>
              <q-item-section>
                <q-item-label
                  >{{ item.firstName }} {{ item.lastName }}
                  {{ item.street }}</q-item-label
                >
                <q-item-label
                  >{{ item.zip }} {{ item.city }}
                  {{ item.country }}</q-item-label
                >
                <q-item-label>{{ item.email }}</q-item-label>
              </q-item-section>
              <q-item-section side>
                <div class="row">
                  <q-btn flat round color="primary" icon="edit" size="md">
                    <q-tooltip>Edit</q-tooltip>
                  </q-btn>
                  <q-btn
                    title="Delete employee"
                    flat
                    round
                    color="primary"
                    icon="delete"
                    size="md"
                  >
                    <q-tooltip>Delete</q-tooltip>
                  </q-btn>
                </div>
              </q-item-section>
            </q-item>
            <q-separator spaced inset="item" v-if="index < data.length - 1" />
          </div>
        </q-list>
        <q-separator />
        <div class="q-pa-md">
          <q-pagination
            v-model="currentPageNo"
            color="primary"
            :max="10"
            :max-pages="6"
            :boundary-numbers="true"
            class="float-left"
          />
          <q-space />
          <div class="float-right">
            26-50 of 1.245
          </div>
        </div>
      </div>
    </template>
  </c-page-layout>
</template>

<script lang="ts">
import Vue from 'vue'
import CAvatar from '../components/Avatar.vue'
import CPageLayout from '../layouts/PageLayout.vue'

export default Vue.extend({
  data() {
    return {
      currentPageNo: 1,

      columns: [
        {
          name: 'name',
          required: true,
          label: 'Dessert (100g serving)',
          align: 'left',
          field: (row: any) => row.name,
          format: (val: any) => `${val}`,
          sortable: true
        },
        {
          name: 'calories',
          align: 'center',
          label: 'Calories',
          field: 'calories',
          sortable: true
        },
        { name: 'fat', label: 'Fat (g)', field: 'fat', sortable: true },
        { name: 'carbs', label: 'Carbs (g)', field: 'carbs' },
        { name: 'protein', label: 'Protein (g)', field: 'protein' },
        { name: 'sodium', label: 'Sodium (mg)', field: 'sodium' },
        {
          name: 'calcium',
          label: 'Calcium (%)',
          field: 'calcium',
          sortable: true,
          sort: (a: string, b: string) => parseInt(a, 10) - parseInt(b, 10)
        },
        {
          name: 'iron',
          label: 'Iron (%)',
          field: 'iron',
          sortable: true,
          sort: (a: string, b: string) => parseInt(a, 10) - parseInt(b, 10)
        }
      ],
      data: [
        {
          firstName: 'Jane',
          lastName: 'Doe',
          email: 'jane.doe@gmail.com'
        },
        {
          firstName: 'John',
          lastName: 'Smith',
          email: 'john.smith@hotmail.com'
        },
        {
          firstName: 'Mary',
          lastName: 'Jackson',
          email: 'mary.jackson@hotmail.com'
        }
      ]
    }
  },

  components: {
    CAvatar,
    CPageLayout
  }
})
</script>

<style lang="scss"></style>
