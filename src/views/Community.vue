<template>
  <div>
    <div class="container">
      <div class="row markdown-body">
        <div class="col-sm-8">
          <loading v-if="seen"></loading>
          <vue-markdown v-if="seen==false" v-bind:source="md" :toc="true" :toc-anchor-link-symbol="toc" :postrender="parse"></vue-markdown>
        </div>
        <my-sidebar/>
      </div>
      <div class="col-sm-8" v-if="this.content()==='Project Committers'">
        <router-link  to="/Development" class="nav-link"><span style="font-size: medium">Want to join us? Learn How to Contribute </span>
        </router-link>
      </div>
    </div>
    <br>
    <br>
    <br>
    <footer-bar/>
  </div>
</template>

<script>
  import Footer from "../components/FooterFixed"
  import SideBar from '../components/SideBar'
  import markdown from 'vue-markdown'
  import axios from 'axios'
  import Golbal from '../components/Global'
  import LoadingBar from '../components/Loading'

  export default {
    name: "Community",
    components: {
      'footer-bar': Footer,
      'my-sidebar': SideBar,
      'vue-markdown': markdown,
      'loading': LoadingBar,
    },
    data() {
      return {
        msg: 'Welcome to Community Page',
        md: "",
        toc: "",
        seen: true
      }
    },
    created() {
      this.fetchData();
    },
    watch: {
      '$route': 'fetchData'
    },
    methods: {
      content: function () {
        return this.$route.params.content
      },
      fetchData() {
        const dict = {
          "Powered By": Golbal.SUPPORT_VERSION[Golbal.DEFAULT_VERSION]['doc-prefix'] +
          Golbal.SUPPORT_VERSION[Golbal.DEFAULT_VERSION]['branch'] +
            "/docs/Community-Powered%20By.md",
          "Project Committers": Golbal.SUPPORT_VERSION[Golbal.DEFAULT_VERSION]['doc-prefix'] +
          Golbal.SUPPORT_VERSION[Golbal.DEFAULT_VERSION]['branch'] +
            "/docs/Community-Project%20Committers.md",
          "History & Vision": Golbal.SUPPORT_VERSION[Golbal.DEFAULT_VERSION]['doc-prefix'] +
          Golbal.SUPPORT_VERSION[Golbal.DEFAULT_VERSION]['branch'] +
            "/docs/Community-History%26Vision.md",
        };
        const content = this.content();
        let url = null;
        if (content in dict) {
          url = dict[content];
        } else {
          this.$router.push('/404');
        }
        const pointer = this;
        this.seen = true;
        axios.get(url)
          .then(function (response) {
            pointer.md = response.data;
            pointer.seen = false;
          })
      },
      parse(html){
        return Golbal.isReadyForPrerender(html)
      }
    }
  }
</script>
<style scoped>
  h1, h2 {
    font-weight: normal;
  }

  body {
    font-family: Georgia, "Times New Roman", Times, serif;
    color: #555;
  }

  .pager > li > a {
    width: 140px;
    padding: 10px 20px;
    text-align: center;
    border-radius: 30px;
  }

  .blog-footer p:last-child {
    margin-bottom: 0;
  }

</style>
