<template>
  <div>
    <v-container class="default-layouts">
      <!-- <v-layout align-center justify-space-between> -->

      <img src="@/assets/SaMoEats.png" contain height="100" />

      <v-row align="center">
        <v-col
          :class="$vuetify.breakpoint.smAndDown ? 'text-center' : ''"
          cols="12"
          md="6"
        >
          <h1
            :style="{
              fontSize: $vuetify.breakpoint.smAndDown ? '25px' : '50px',
            }"
          >
            Skip the queue — quick and easy collection made for you!
          </h1>

          <p>
            Say goodbye to long lines and delays — our quick and easy collection
            service is designed to get you what you need effortlessly and on
            your schedule.
          </p>
        </v-col>

        <v-col cols="12" md="" class="d-flex justify-center">
          <img src="@/assets/SaMoHome.png" contain height="300" />
        </v-col>
      </v-row>
    </v-container>

    <!-- download app buttons -->
    <div
      class="black d-flex flex-column align-center justify-center text-center py-md-10 pb-5 pt-2 mt-10 px-2"
    >
      <h1 class="green--text">Download Now!</h1>
      <p class="green--text">Get the best mobile experience with our app.</p>

      <v-btn
        class="mt-md-5 green"
        :width="$vuetify.breakpoint.smAndDown ? '100%' : '50%'"
        height="50"
        @click="goToPlayStore"
      >
        DOWNLOAD ON PLAYSTORE
      </v-btn>

      <!-- <v-btn class="mt-5 green" :width="$vuetify.breakpoint.smAndDown ? '100%' : '50%'" height="50">
        DOWNLOAD ON APP STORE
      </v-btn> -->
    </div>

    <div style="background-color: #faf8f9" class="d-flex justify-center">
      <v-container class="text-center">
        <div>
          <canvas ref="qrcodeCanvas"></canvas>
          <h4>Android QRCode</h4>
        </div>

        <h1
          class="mt-4 mb-5"
          :style="{ fontSize: $vuetify.breakpoint.smAndDown ? '20px' : '30px' }"
        >
          SamoEats lets you enjoy your favorite meals without the wait!
        </h1>
        <p clas="mt-16">
          With SamoEats, you can order your food and collect it at your
          convenience — no more waiting in line. Whether you're on the go or
          just looking to save time, we've made the process quick, easy, and
          hassle-free. Experience the future of food collection with SamoEats
          today!
        </p>

        <img
          src="@/assets/SaMoEatsFeatureGraphic.png"
          contain
          :height="$vuetify.breakpoint.smAndDown ? 150 : 350"
        />
      </v-container>
    </div>

    <v-footer
      class="text-center white--text black py-5"
      style="background-color: #faf8f9"
    >
      <v-container>
        <div>
          <p>
            If you want to add your store, contact us at
            <a href="mailto:email@example.com">email@example.com</a>
          </p>
          <p>
            If you have any questions or want to consult about your order, feel
            free to reach out to us!
          </p>
        </div>

        <div>
          <v-row justify="center">
            <v-col class="d-flex" cols="auto">
              <a href="https://facebook.com" target="_blank">Facebook</a> |
              <a
                href="https://www.linkedin.com/company/107037587/admin/inbox/"
                target="_blank"
                >LinkedIn</a
              >
            </v-col>
          </v-row>
        </div>

        <div>
          <p>&copy; 2024 SamoEats. All rights reserved.</p>
        </div>
      </v-container>
    </v-footer>
  </div>
</template>

<script>
import QRCode from "qrcode";

export default {
  name: "OrdersPage",

  components: {
    QRCode,
  },

  data: () => ({
    googlePlayStorUrl:
      "https://www.linkedin.com/company/107037587/admin/inbox/",
  }),

  mounted() {
    QRCode.toCanvas(
      this.$refs.qrcodeCanvas,
      this.googlePlayStorUrl,
      { width: 200 },
      (error) => {
        if (error) console.error(error);
      }
    );
  },

  methods: {
    // goToPlayStore
    goToPlayStore() {
      window.open(this.googlePlayStorUrl, "_blank");
    },
  },
};
</script>

<style lang="scss" scoped>
//
input {
  margin-bottom: 10px;
  padding: 5px;
}

.default-layout {
  width: 1400px;
}

.title {
  font-size: 100px;
  font-weight: 900;
  line-height: 26px;
}
</style>
