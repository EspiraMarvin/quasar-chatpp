<template>
  <q-page class="flex q-pa-md">
    <q-list
      class="full-width"
      separator
    >
      <q-item
        v-for="(user, key) in users"
        :key="key"
        :to="'/chat/' + key"
        clickable
        v-ripple>
        <q-item-section avatar>
          <q-avatar color="primary" text-color="white">
<!--            charAt(0) -grabs the first character/letter from the name -->
            {{ user.name | firstChar }}
          </q-avatar>
        </q-item-section>

        <q-item-section>
          <q-item-label>{{ user.name }}</q-item-label>
        </q-item-section>

        <q-item-section side>
          <q-badge
            :color="user.online ? 'light-green-5' : 'grey-8' "
          >
            {{ user.online ? 'Online' : 'Offline' }}
          </q-badge>
        </q-item-section>
      </q-item>

    </q-list>
  </q-page>
</template>

<script>
import { mapGetters } from 'vuex'
export default {
  computed: {
    ...mapGetters('chatstore', ['users'])
  },
  filters: {
    firstChar (val) {
      return val.charAt(0)
    }
  }
}
</script>

<style>

</style>
