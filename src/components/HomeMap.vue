<template>
  <v-card
    color="blue-grey darken-1"
    dark
    :loading="isUpdating"
  >
    <template v-slot:progress>
      <v-progress-linear
        absolute
        color="green lighten-3"
        height="4"
        indeterminate
      ></v-progress-linear>
    </template>
    <v-img
    >
      <v-row>
        <v-col
          class="text-right"
          cols="12"
        >
          <v-menu
            bottom
            left
            transition="slide-y-transition"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                icon
                v-bind="attrs"
                v-on="on"
              >
                <v-icon>mdi-dots-vertical</v-icon>
              </v-btn>
            </template>
            <v-list>
              <v-list-item @click="isUpdating = true">
                <v-list-item-action>
                  <v-icon>mdi-cog</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                  <v-list-item-title>Update</v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-list>
          </v-menu>
        </v-col>
        <v-row
          class="pa-4"
          align="center"
          justify="center"
        >
          <v-col class="text-center">
            <h3 class="headline">
              {{ name }}
            </h3>
            <span class="grey--text text--lighten-1">{{ title }}</span>
          </v-col>
        </v-row>
      </v-row>
    </v-img>
    <v-form>
      <v-container>
        <v-row>
          <v-col
            cols="12"
            md="6"
          >
            <v-text-field
              v-model="name"
              :disabled="isUpdating"
              filled
              color="blue-grey lighten-2"
              label="Name"
            ></v-text-field>
          </v-col>
          <v-col
            cols="12"
            md="6"
          >
            <v-text-field
              v-model="title"
              :disabled="isUpdating"
              filled
              color="blue-grey lighten-2"
              label="Title"
            ></v-text-field>
          </v-col>
          <v-col cols="12">
            <v-autocomplete
              v-model="friends"
              :disabled="isUpdating"
              :items="people"
              filled
              chips
              color="blue-grey lighten-2"
              label="Selectionner"
              item-text="name"
              item-value="name"
              multiple
            >
              <template v-slot:selection="data">
                <v-chip
                  v-bind="data.attrs"
                  :input-value="data.selected"
                  close
                  @click="data.select"
                  @click:close="remove(data.item)"
                >
                  <v-avatar left>
                    <v-img :src="data.item.avatar"></v-img>
                  </v-avatar>
                  {{ data.item.name }}
                </v-chip>
              </template>
              <template v-slot:item="data">
                <template v-if="typeof data.item !== 'object'">
                  <v-list-item-content v-text="data.item"></v-list-item-content>
                </template>
                <template v-else>
                  <v-list-item-avatar>
                    <img :src="data.item.avatar">
                  </v-list-item-avatar>
                  <v-list-item-content>
                    <v-list-item-title v-html="data.item.name"></v-list-item-title>
                    <v-list-item-subtitle v-html="data.item.group"></v-list-item-subtitle>
                  </v-list-item-content>
                </template>
              </template>
            </v-autocomplete>
          </v-col>
        </v-row>
      </v-container>
    </v-form>
    <v-divider></v-divider>
    <v-card-actions>
      <v-switch
        v-model="autoUpdate"
        :disabled="isUpdating"
        class="mt-0"
        color="green lighten-2"
        hide-details
        label="Auto Update"
      ></v-switch>
      <v-spacer></v-spacer>
      <v-btn
        :disabled="autoUpdate"
        :loading="isUpdating"
        color="blue-grey darken-3"
        depressed
        @click="isUpdating = true"
      >
        <v-icon left>
          mdi-update
        </v-icon>
        Update Now
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
    name: 'HomeMap',
     data () {
      const srcs = {
        1: 'http://source.unsplash.com/RLQ0YYzQuis',
        2: 'http://source.unsplash.com/JNTSoyb_bbw',
        3: 'http://source.unsplash.com/m3th3rIQ9-w',
        4: 'http://source.unsplash.com/z99Z1SL67HE',
        5: 'http://source.unsplash.com/OcKeEdgzVuU',
        6: 'http://source.unsplash.com/DfRhinJk7fw',
        7: 'http://source.unsplash.com/QIGfGevKSQo',
        8: 'http://source.unsplash.com/2lMK4dgqwFM'
      }

      return {
        autoUpdate: true,
        friends: ['Sandra Adams', 'Britta Holt'],
        isUpdating: false,
        name: 'Midnight Crew',
        people: [
          { header: 'Sites Culturels à proximités' },
          { name: 'Musées', group: 'Sites Culturels', avatar: srcs[1] },
          { name: 'Galerie dArt', group: 'Sites Culturels', avatar: srcs[2] },
          { name: 'Théâtres', group: 'Sites Culturels', avatar: srcs[3] },
          { name: 'Parcs', group: 'Sites Culturels', avatar: srcs[4] },
          { name: 'Boîtes de Nuit', group: 'Sites Culturels', avatar: srcs[3] },
          { divider: true },
          { header: 'Edifices Religieux à proximités' },
          { name: 'Eglises', group: 'Edifices Religieux', avatar: srcs[4] },
          { name: 'Synagogue', group: 'Edifices Religieux', avatar: srcs[5] },
          { name: 'Mosquées', group: 'Edifices Religieux', avatar: srcs[1] },
          
        ],
        
      }
    },

    watch: {
      isUpdating (val) {
        if (val) {
          setTimeout(() => (this.isUpdating = false), 3000)
        }
      },
    },

    methods: {
      remove (item) {
        const index = this.friends.indexOf(item.name)
        if (index >= 0) this.friends.splice(index, 1)
      },
    },
  };
</script>

<style scoped>
</style>