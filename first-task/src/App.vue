<template>
  <v-app >
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <h2>First-Task</h2>
      </div>

      <v-spacer></v-spacer>

      <v-btn target="_blank" text>
        <span class="mr-2">Sign out</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-content >
      <v-row style="display: flex; justifyContent: center">
        <v-col sm="8" class="main-container">
          <v-container style="paddingBottom: 30px">
            <v-row style="display: flex; alignItems: center; justifyContent: center">
              <v-col cols="8" style="display: flex; alignItems: center; justifyContent: center; flexDirection: column">
                <v-progress-circular
                  :rotate="-90"
                  :size="150"
                  :width="12"
                  :value="progressValue"
                  color="#C51162"
                  style="fontWeight: bold; fontSize: 25px"
                >
                  {{ progressValue }}%
                </v-progress-circular>
                <div style="display: flex; alignItems: center; justifyContent: center">
                  <v-icon small color="#C51162">mdi-flag-variant</v-icon>
                  <h5 style="color: #C51162; margin: 5px 0">Quotes added</h5>
                </div>
              </v-col>
            </v-row>
            <v-row class="card" style="display: flex; alignItems: center; justifyContent: center">
              <v-col cols="8" >
                <v-textarea
                  outlined
                  name="input-7-4"
                  label="Write Your Quote"
                  height="100"
                  v-model="textAreaValue"
                ></v-textarea>
                <v-btn rounded block height="25" style="margin-top: -10px" dark @click="addItem()">Add Item</v-btn>
              </v-col>
            </v-row>
            <v-divider style="margin: 20px"></v-divider>
            <v-row>
              <v-col>
                <v-list >
                  <v-list-item-group  color="primary">
                    <v-list-item>
                      <v-list-item-content style="padding: 3px 10px">
                        <div>
                          <v-alert
                            prominent
                            dense
                            color="#1976D2"
                            border="left"
                            elevation="4"
                            colored-border
                            icon="mdi-format-quote-close"
                            v-for="item in arrayOfItems" :key="item"
                            
                          >
                            <v-row align="center">
                              <v-col class="grow" >{{ item }}</v-col>
                              <v-btn class="mx-2" fab icon x-small  color="primary" @click="deleteItem" >
                                <v-icon dark>mdi-window-close</v-icon>
                              </v-btn>
                            </v-row>
                          </v-alert>
                        </div> 
                      </v-list-item-content> 
                    </v-list-item>
                  </v-list-item-group>
                </v-list>
              </v-col>
            </v-row>
          </v-container>
        </v-col>
      </v-row>
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      textAreaValue: '',
      progressValue: 0,
      arrayOfItems: [],
    }
  },
  methods: {
    addItem() {
      if ( this.textAreaValue.length > 0 && this.arrayOfItems.length <= 9 ) {
        this.arrayOfItems.push(this.textAreaValue);
        this.textAreaValue = ''
        this.progressValue += 10;
        // console.log(this.arrayOfItems)
      }else return;
    },
    deleteItem() {
      this.arrayOfItems.pop();
      // for(var i = this.arrayOfItems.length - 1; i >= 0; i--) {
      //   if(this.arrayOfItems[i] === item) {
      //       this.arrayOfItems.splice(i, 1);
      //   }
      // }
      this.progressValue -= 10;
      // console.log(this.arrayOfItems)
    }
  }
};
</script>

<style lang="css">
  .main-container {
    margin-top: 80px;
    margin-bottom: 80px;
    border: 2px solid #000;
    border-radius: 20px 0 20px 0;
    box-shadow: 0 1px 15px rgba(0,0,0,.3);
  }
</style>