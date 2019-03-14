<template>
  <v-app class="page-background">
    <v-toolbar co app flat color="white" class="top-toolbar">
      <v-toolbar-title class="headline text-uppercase">
        <img src="@/assets/logo.png">
      </v-toolbar-title>
      <v-spacer></v-spacer>

        <v-btn-toggle value="active">
          <v-btn
            flat
          >
            <span class="mr-2">HOME</span>
          </v-btn>
          <v-btn
            flat
          >
            <span class="mr-2">UBER UNS</span>
          </v-btn>
          <v-btn
            flat
            value="active"
          >
            <span class="mr-2">PRODUKTE</span>
          </v-btn>
          <v-btn
            flat
          >
            <span class="mr-2">REFERENZEN</span>
          </v-btn>
          <v-btn
            flat
          >
            <span class="mr-2">KONTAKT</span>
          </v-btn>
        </v-btn-toggle>

        <a href="#" class="primary-color">DE</a>&nbsp;/&nbsp;FR
      </div>
    </v-toolbar>


    <v-content class="main-content">
      <v-card flat class="mt-5 mb-4">

        <v-card-title primary-title>
          <div>
            <h3 class="headline mb-0"><strong>PRODUKTE</strong></h3>
          </div>
        </v-card-title>
        <v-divider class="mx-3"></v-divider>

        <v-breadcrumbs :items="items" >
          <template v-slot:divider>
            <v-icon>forward</v-icon>
          </template>
        </v-breadcrumbs>

        <div class="py-3">
          <template v-for="(product, index) in productData">
            <v-card flat :class="{'odd-background': index%2 }" class="py-4">
              <v-layout>
                <v-flex xs3>
                  <v-img
                    :src="product.img_url || 'https://cdn.vuetifyjs.com/images/cards/foster.jpg'"
                    contain
                    class="mx-3"
                  ></v-img>
                </v-flex>
                <v-flex xs9>
                  <v-card-title primary-title>
                    <div>
                      <div class="title">{{product.title}}</div>
                      <div class="subheading">{{product.sub_title}}</div>
                      <div class="body-1 mt-2">{{product.description}}</div>
                    </div>
                  </v-card-title>

                  <v-card-actions class="card-btn">
                    <v-btn flat class="primary-color-background">Mehr Erfahren <v-icon>keyboard_arrow_right</v-icon></v-btn>
                  </v-card-actions>
                </v-flex>

              </v-layout>
            </v-card>
          </template>
        </div>
      </v-card>
    </v-content>

    <v-footer color="white" height="auto" class="footer-content py-4">
      <v-layout
        justify-center
        row
        wrap>
        <v-flex class="footer-column">
          &copy; Eig Crustag 2014
          <br>
          Impressum
        </v-flex>   
        <v-flex class="footer-column">
        </v-flex>
        <v-flex class="footer-column">
          <p>Buro Baar ZG</p>
          <div class="my-2"><v-icon class="footer-numbers mr-2">phone_iphone</v-icon> <div class="d-inline">(Tel) +41 22 735 95 00</div></div>
          <div class="mt-3"><v-icon class="footer-numbers mr-2">print</v-icon><div class="d-inline">(Fax) +41 22 786 96 00</div></div>
          <div class="my-1"><v-icon class="footer-location mr-2">location_on</v-icon><div class="d-inline-block">Route deFrontenex 120, <br> 1208 Geneve</div></div>
        </v-flex>    
        <v-flex class="footer-column">
          <p>Buro Geneve</p>
          <div class="my-2"><v-icon class="footer-numbers mr-2">phone_iphone</v-icon> <div class="d-inline">(Tel) +41 22 735 95 00</div></div>
          <div class="mt-3"><v-icon class="footer-numbers mr-2">print</v-icon><div class="d-inline">(Fax) +41 22 786 96 00</div></div>
          <div class="my-1"><v-icon class="footer-location mr-2">location_on</v-icon><div class="d-inline-block">Route deFrontenex 120, <br> 1208 Geneve</div></div>
        </v-flex>   
      </v-layout>
    </v-footer>

  </v-app>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      productData: [],
      items: [
        {
          text: 'Home',
          disabled: true,
          href: 'breadcrumbs_dashboard'
        },
        {
          text: 'Warme / Kalte',
          disabled: true,
          href: 'breadcrumbs_link_1'
        },
        {
          text: 'Automatikfilter',
          disabled: true,
          href: 'breadcrumbs_link_2'
        }
      ]
    }
  },
  mounted(){
    this.$axios.get('/products').then(res => {
      this.productData = res.data.data
    })
  }
}
</script>

<style>
  *{
    font-family: "Arial", Times, serif;
  }
  .top-toolbar{
    padding: 12px 260px !important;
  }
  .top-toolbar .v-toolbar__content{
    padding: 0 !important;
  }
  .main-content{
    margin-top: 12px;
    padding-left: 260px !important;
    padding-right: 260px !important;
  }
  .footer-content{
    padding-left: 260px !important;
    padding-right: 260px !important;
  }
  .page-background{
    background-color: rgb(223, 220, 216) !important;
    border-color: rgb(223, 220, 216) !important;
  }
  .primary-color{
    color: rgb(225, 95, 95) !important;
  }
  .primary-color-background{
    background-color: rgb(225, 95, 95) !important;
    color: rgb(255, 255, 255) !important;
    border-radius: 0;
  }
  .footer-column{
    width: 90px !important;
  }
  .footer-location{
    line-height: 2;
  }
  .footer-numbers{
   line-height: .5; 
  }

  .v-item-group .v-btn{
    border-top: 2px solid rgb(223, 220, 216);
  }
  .v-item-group .v-btn--active span{
    color: rgb(225, 95, 95) !important; 
  }
  .v-item-group .v-btn--active{
    border-top: 6px solid rgb(225, 95, 95);
    color: white !important;
    background: white !important;
  }
  .odd-background{
    background-color: rgb(245, 245, 245) !important; 
    border-color: rgb(245, 245, 245) !important; 
  }
  .card-btn{
    position: absolute;
    bottom: 20px;
    right: 15px;
  }
</style>
