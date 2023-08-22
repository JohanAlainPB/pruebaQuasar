<template>
  <div class="q-pa-md">
    <q-card class="my-card" flat bordered>
      <q-tabs v-model="tab" class="text-teal">
        <q-tab label="Prioritarios" name="one" />
        <q-tab label="Todos" name="two" />
      </q-tabs>

      <q-separator />

      <q-tab-panels v-model="tab" animated>
        <q-tab-panel name="one">
          <q-list bordered>
            <q-item v-for="contact in contacts" :key="contact.id" class="q-my-sm" clickable v-ripple>
              <q-item-section avatar>
                <q-avatar color="primary" text-color="white">
                  {{ contact.letter }}
                </q-avatar>
              </q-item-section>

              <q-item-section>
                <q-item-label>{{ contact.name }}</q-item-label>
                <q-item-label caption lines="1">{{ contact.email }}</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-tab-panel>

        <q-tab-panel name="two">
          With so much content to display at once, and often so little screen real-estate,
          Cards have fast become the design pattern of choice for many companies, including
          the likes of Google and Twitter.
        </q-tab-panel>
      </q-tab-panels>
    </q-card>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    return {
      tab: ref('one'),
      contacts
    }
  }
}

const contacts = [{
  id: 1,
  name: 'Ruddy Jedrzej',
  email: 'rjedrzej0@discuz.net',
  letter: 'R'
}]

</script>

<style lang="scss" scoped>
.my-card{
  display: flex;
  flex-direction: column;
}
</style>
