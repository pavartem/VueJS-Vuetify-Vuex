<template>
    <v-container>
        <v-layout row>
            <v-flex xs12 sm6 offset-sm3>
                <h1 class="text--secondary mb-3">Create new ad</h1>
                <v-form v-model="valid" ref="form" validation>
                    <v-text-field
                            name="title"
                            label="Ad title"
                            type="text"
                            v-model="title"
                            :rules="[v => !!v || 'Title is required']"
                    ></v-text-field>
                    <v-text-field
                            id="description"
                            name="description"
                            label="Description"
                            type="text"
                            multi-line
                            v-model="description"
                            :rules="[v => !!v || 'Description is required']"
                    ></v-text-field>
                </v-form>
                <v-layout class="mb-3 mt-2">
                    <v-flex xs12>
                        <v-btn
                                :loading="loading3"
                                :disabled="loading3"
                                color="primary"
                                class="white--text"
                                @click.native="loader = 'loading3'"
                        >
                            Upload
                            <v-icon right dark>cloud_upload</v-icon>
                        </v-btn>
                    </v-flex>
                </v-layout>
                <v-layout>
                    <v-flex xs12>
                        <img src="" height="100" alt="">
                    </v-flex>
                </v-layout>

                <v-layout>
                    <v-flex xs12>
                        <v-switch
                                color="primary"
                                label="Add to promo ?"
                                v-model="promo"
                        ></v-switch>
                    </v-flex>
                </v-layout>

                <v-layout>
                    <v-flex xs12>
                        <v-spacer></v-spacer>
                        <v-btn
                                :disabled="!valid"
                                class="success"
                                @click="createAd"
                        >Create ad</v-btn>
                    </v-flex>
                </v-layout>


            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
  export default {
    data () {
      return {
        title: '',
        description: '',
        promo: false,
        valid: false
      }
    },
    methods: {
      createAd() {
        if (this.$refs.form.validate()) {
          const ad = {
            title: this.title,
            description: this.description,
            promo: this.promo
          }
          console.log(ad)
        }
      }
    }
  }
</script>

<style scoped>

</style>
