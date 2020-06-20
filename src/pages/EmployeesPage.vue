<template>
  <q-card class="q-ma-md">
    <q-card-section horizontal>
      <q-card-section>
        <div class="text-h6">Employees</div>
      </q-card-section>
      <q-card-section>
        <q-btn round color="primary">
          <q-icon name="add" size="xs" />
        </q-btn>
      </q-card-section>
    </q-card-section>
    <q-separator />
    <q-card-section>
      <q-list>
        <div v-for="(item, index) in data" :key="item.name">
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <c-avatar :firstName="item.firstName" :lastName="item.lastName" />
            </q-item-section>
            <q-item-section>
              <q-item-label
                >{{ item.firstName }} {{ item.lastName }}
                {{ item.street }}</q-item-label
              >
              <q-item-label
                >{{ item.zip }} {{ item.city }} {{ item.country }}</q-item-label
              >
              <q-item-label>{{ item.email }}</q-item-label>
            </q-item-section>
            <q-item-section side>
              <div class="row">
                <q-btn flat round color="primary" icon="edit" size="md">
                  <q-tooltip>Edit employee</q-tooltip>
                </q-btn>
                <q-btn
                  title="Delete employee"
                  flat
                  round
                  color="primary"
                  icon="delete"
                  size="md"
                >
                  <q-tooltip>Delete employee</q-tooltip>
                </q-btn>
              </div>
            </q-item-section>
          </q-item>
          <q-separator spaced inset="item" v-if="index < data.length - 1" />
        </div>
      </q-list>
      <!--
    <q-table
      title="Employees"
      dense
      :data="data"
      :columns="columns"
      row-key="name"
    />
    -->
    </q-card-section>
    <q-separator />
    <q-card-section class="q-pa-sm vertical-middle" horizontal>
      <q-card-section horizontal>
        <q-pagination
          v-model="currentPageNo"
          color="primary"
          :max="10"
          :max-pages="6"
          :boundary-numbers="true"
        />
      </q-card-section>
      <q-space />
      <q-card-section horizontal>
        26-50 of 1.245
      </q-card-section>
    </q-card-section>
  </q-card>
</template>

<script lang="ts">
import Vue from 'vue'
import CAvatar from '../components/Avatar.vue'

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
    CAvatar
  }
})
</script>

<style lang="scss"></style>
