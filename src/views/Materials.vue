<template>
  <div>
    <div class="container">
      <div class="row markdown-body">
        <div class="col-sm-8">

          <h2>Other Materials</h2>
          <ul>
            <li style="margin: 5px;">
              <a style="font-size: 16px"
                 href="https://github.com/apache/incubator-iotdb/blob/master/docs/Documentation/OtherMaterial-Sample%20Data.txt">Sample Data</a>
            </li>
            <li v-for="item in items" style="margin: 5px">
              <router-link :to="item.url" style="font-size: 16px">{{item.content}}</router-link>
            </li>
          </ul>
        </div>
        <my-sidebar/>
      </div>
    </div>

    <footer-bar/>
  </div>
</template>

<script>
  import Footer from "../components/FooterFixed"
  import SideBar from '../components/SideBar'

  export default {
    name: "Materials",
    components: {
      'footer-bar': Footer,
      'my-sidebar': SideBar
    },
    data() {
      return {
        items: [
          {'content': "Release Notes", 'url': "/Materials/Release Notes", "isDownloadable" : false},
          {'content': "Examples", 'url': "/Example", "isDownloadable" : false},
          {'content': "References", 'url': "/Materials/References","isDownloadable" : false},
        ]
      }
    },
  }
</script>

<style scoped>
  .main>div {
    margin-top: 10px;
  }

  li {
    font-size: 16px;
  }
</style>
