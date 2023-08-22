<template>
  <q-layout view="hHh lpR fff">
    <q-header reveal bordered class="bg-primary text-white q-pb-lg" height-hint="98">
      <q-toolbar>
        <q-toolbar-title align="left">
          <q-btn flat label="Inicio" />
          <q-btn flat label="Vista" />
          <q-btn flat label="Ayuda" />
        </q-toolbar-title>
      </q-toolbar>

      <q-tabs align="left">
        <q-btn class="q-ml-lg" flat icon="menu" @click="toggleRightDrawer" />
        <q-btn-dropdown split flat icon="ti-email" label="Correo nuevo" class="bg-secondary" />
        <q-btn flat to="/page2" icon="ti-trash" label="Eliminar" />
        <q-btn flat to="/page2" icon="ti-archive" label="Archivar" />
        <q-btn flat to="/page2" icon="ti-info-alt" label="Informar" />
        <q-btn flat to="/page2" icon="ti-paint-roller" label="Limpiar" />
        <!-- Agrega más botones según tus necesidades -->
      </q-tabs>
    </q-header>

<!--DRAWNER-->
    <q-drawer show-if-above side="left" bordered>
      <!--FAVORITOS-->
      <div class="q-pa-md" align="center">
        <q-btn-dropdown flat label="Favoritos" @show="onFavoritosDropdownShow" @hide="onFavoritosDropdownHide">
          <q-list class="custom-list">
            <q-item clickable @click="onItemClick" >
              <q-item-section>
                <q-item-label><q-icon name="ti-email" /> Bandeja de entrada</q-item-label>
              </q-item-section>
            </q-item>

            <q-item clickable @click="onItemClick">
              <q-item-section>
                <q-item-label><q-icon name="ti-new-window" /> Elementos enviados</q-item-label>
              </q-item-section>
            </q-item>

            <q-item clickable @click="onItemClick">
              <q-item-section>
                <q-item-label><q-icon name="ti-pencil" /> Borradores</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-btn-dropdown>
      </div>
      <!--CARPETAS-->
      <div class="q-pa-md" align="center">
        <q-btn-dropdown flat label="Carpetas" :style="{ marginTop: dropdownMargin }">
          <q-list>
            <q-item clickable @click="onItemClick">
              <q-item-section>
                <q-item-label><q-icon name="ti-email" /> Bandeja de entrada</q-item-label>
              </q-item-section>
            </q-item>

            <q-item clickable @click="onItemClick">
              <q-item-section>
                <q-item-label><q-icon name="ti-pencil" /> Borradores</q-item-label>
              </q-item-section>
            </q-item>

            <q-item clickable @click="onItemClick">
              <q-item-section>
                <q-item-label><q-icon name="ti-new-window" /> Elementos enviados</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-btn-dropdown>
      </div>
    </q-drawer>

    <q-drawer show-if-above side="right" bordered width="1100">
      <!-- drawer content -->
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script>
export default {
  data () {
    return {
      leftDrawerOpen: false,
      favoritosDropdownOpen: false,
      dropdownMargin: '0'
    }
  },
  methods: {
    onFavoritosDropdownShow () {
      this.favoritosDropdownOpen = true
      this.adjustCarpetasDropdownPosition()
    },
    onFavoritosDropdownHide () {
      this.favoritosDropdownOpen = false
      this.adjustCarpetasDropdownPosition()
    },
    adjustCarpetasDropdownPosition () {
      if (this.favoritosDropdownOpen) {
        this.dropdownMargin = '130px'
      } else {
        this.dropdownMargin = '0'
      }
    }
  }
}
</script>

<style >

</style>
