<template>
  <section class="content-wrapper" style="min-height: 960px;">
    <section class="content-header">
      <h1>Country</h1>
    </section>

    <section class="content">
      <div class="row">
        <div class="col-xs-12">
          <div class="box">
            <div class="box-header with-border">
              <h3 class="box-title">View</h3>
            </div>

            <div class="box-body">
              <back-buttton></back-buttton>
            </div>

            <div class="box-body">
              <div class="row" v-if="loading">
                <div class="col-xs-4 col-xs-offset-4">
                  <div class="alert text-center">
                    <i class="fa fa-spin fa-refresh"></i> Loading
                  </div>
                </div>
              </div>
              <div class="row" v-if="!loading">
                <div class="col-xs-6">
                  <table class="table table-bordered table-striped">
                    <tbody>
                      <tr>
                        <th>#</th>
                        <td>{{ item.id }}</td>
                      </tr>
                      <tr>
                        <th>Country Name</th>
                        <td>{{ item.name }}</td>
                      </tr>
                      <tr>
                        <th>Country Code(ISO)</th>
                        <td>{{ item.code }}</td>
                      </tr>
                      <tr>
                        <th>Initial Price</th>
                        <td>{{ item.initial_price + item.currency.symbol + '(' + item.currency.code + ')' }}</td>
                      </tr>
                      <tr>
                        <th>Extra Price</th>
                        <td>{{ item.extra_price + item.currency.symbol + '(' + item.currency.code + ')' }}</td>
                      </tr>
                      <tr>
                        <th>Activated</th>
                        <td>{{item.activated == 1}}</td>
                      </tr>
                    </tbody>
                  </table>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </section>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  data() {
    return {
      // Code...
    };
  },
  created() {
    this.fetchData(this.$route.params.id);
  },
  destroyed() {
    this.resetState();
  },
  computed: {
    ...mapGetters("CountriesSingle", ["item", "loading"])
  },
  watch: {
    "$route.params.id": function() {
      this.resetState();
      this.fetchData(this.$route.params.id);
    }
  },
  methods: {
    ...mapActions("CountriesSingle", ["fetchData", "resetState"])
  }
};
</script>

<style scoped>
</style>
