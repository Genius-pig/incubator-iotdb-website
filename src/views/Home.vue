<template>
  <div>
    <div class="main container">
      <div class="row">
        <div class="col-md-9 col-sm-9">
          <div>
            <p class="home-tittle">Apache IoTDB (incubating) (Database for Internet of Things)</p>
            <article lang="en">
              <p>Apache IoTDB (incubating) (Database for Internet of Things) is an integrated data
                management engine designed for timeseries data. It provides users with services for
                data collection, storage and analysis. Due to its light-weight architecture, high
                performance and rich feature set together with its deep integration with Apache
                Hadoop and Spark, Apache IoTDB (incubating) can meet the requirements of massive
                data storage, high-speed data ingestion and complex data analysis in the IoT
                industrial fields.
              </p>
              <p>
                Apache IoTDB (incubating) was initially developed by Prof. Wang's Team of School of
                Software at Tsinghua University. Now it is an effort undergoing incubation at The
                Apache Software Foundation (ASF), sponsored by the Incubator.
              </p>
            </article>
          </div>
          <div>
            <p class="home-tittle">Scenarios</p>
            <div id="myCarousel" class="carousel slide" data-ride="carousel" style="background: rgb(31,31,31)">
              <ol class="carousel-indicators">
                <li data-target="#myCarousel" data-slide-to="0" class="active"></li>
                <li data-target="#myCarousel" data-slide-to="1"></li>
                <li data-target="#myCarousel" data-slide-to="2"></li>
              </ol>
              <div class="carousel-inner">
                <div class="item active">
                  <img src="https://user-images.githubusercontent.com/1021782/50463652-f67c6480-09c7-11e9-8f65-c8adaff09043.png" alt="First slide">
                  <br/>
                  <div class="Scenarios">
                    <h1>High-end equipment</h1>
                    <article lang="en">
                      <p> In high-end manufacturing, there are many devices equipped with sensors collecting working status data.
                        Meteorological stations, wind turbines are common high-end devices.
                        These devices, if supports Java or Go (in developing), can run TsFile to store data locally.
                        In this way, TsFile can provide the ability to save data with high throughput, high compression ratio, and millisecond query.
                        Together with TsFile-Sync tool, TsFiles can be transmitted to the data center.
                      </p>
                    </article>
                  </div>
                </div>
                <div class="item">
                  <img src="https://user-images.githubusercontent.com/1021782/50463651-f67c6480-09c7-11e9-9374-3e6c6c540d7b.png" alt="Second slide">
                  <br/>
                  <div class="Scenarios">
                    <h1>Local Controller</h1>
                    <article lang="en">
                      <p>
                        In the scene of factories, there are tens of devices under LAN network.
                        IoTDB can be installed on a local controller server in the factory to receive data from those devices.
                        The local controller server (normal PC or workstation) with IoTDB can provide the ability to persist data and query data with SQL-like interface.
                        In addition, with TsFile-Sync tool, TsFiles on the local controller can be transmitted to the data center equipped with IoTDB instance in the cloud.
                      </p>
                    </article>
                  </div>
                </div>
                <div class="item">
                  <img src="https://user-images.githubusercontent.com/1021782/50463650-f67c6480-09c7-11e9-9b80-bc66aa5dc0ab.png" alt="Third slide">
                  <br/>
                  <div class="Scenarios">
                    <h1>Cloud Data Management</h1>
                    <article lang="en">
                      <p>
                        In the scene of high-speed network (Internet of Vehicles, etc.), a car installed sensors on it can collect monitoring information(driving status, etc.) of itself at a certain frequency.
                        Usually, these automotive devices have limited hardware configurations and are difficult to carry complex applications.
                        Lightweight IoTDB(IoTDB Client) came into being.
                        With JDBC API, it can make data sent by narrow-band IoT or 4G possible. In this way, devices and cloud are connected together.
                      </p>
                    </article>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div>
            <p class="home-tittle" style="padding-top: 15px">Main Features</p>
            <div class="row feature">
              <div class="col-lg-4 col-md-4 col-sm-6 col-xs-12 feature-item" v-for="item in featureBlock1" @mouseover="hover($event)"
                   @mouseleave="unhover($event)">
                <div class="row feature-title-row">
                  <div class="col-xs-2 col-sm-2">
                    <img :src=item.featureSrc style="vertical-align:middle">
                  </div>
                  <div class="col-xs-10 col-sm-10 feature-title"><p>{{item.featureTitle}}</p></div>
                </div>
                  <p class="feature-content" style="text-align: justify">{{item.featureContent}}</p>
                <hr/>
              </div>
            </div>
          </div>
        </div>
        <side-bar/>
      </div>

    </div>
    <footer-bar/>
  </div>
</template>

<script>
  import SideBar from "../components/SideBar";
  import Footer from "../components/FooterFixed"
  export default {
    name: "Home",
    components: {
      'side-bar': SideBar,
      'footer-bar': Footer
    },
    data() {
      return {
        msg: 'Welcome to Home Page',
        featureBlock1: [
          {
            featureSrc: require("../assets/img/home-icon1.png"), featureTitle: "High-throughput read and write",
            featureContent: "Apache IoTDB (incubating) can support high-speed write access for millions of low-power and intelligently networked devices. It also provides lightning read access for retrieving data."
          },
          {
            featureSrc: require("../assets/img/home-icon2.png"), featureTitle: "Efficient directory structure",
            featureContent: "Apache IoTDB (incubating) can efficiently organize complex data structure from IoT devices and large size of timeseries data with fuzzy searching strategy for complex directory of timeseries data."
          },
          {
            featureSrc: require("../assets/img/home-icon3.png"), featureTitle: "Rich query semantics",
            featureContent: "Apache IoTDB (incubating) can support time alignment for timeseries data across devices and sensors, computation in timeseries field and abundant aggregation functions in time dimension."
          },
          {
            featureSrc: require("../assets/img/home-icon4.png"), featureTitle: "Low cost on hardware",
            featureContent: "Apache IoTDB (incubating) can reach a high compression ratio of disk storage (it costs less than $0.23 to store 1GB of data on hard disk)."
          },
          {
            featureSrc: require("../assets/img/home-icon5.png"), featureTitle: "Flexible deployment",
            featureContent: "Apache IoTDB (incubating) can provide users one-click installation tool on the cloud, terminal tool on desktop and the bridge tool between cloud platform and on premise machine (Data Synchronization Tool)."
          },
          {
            featureSrc: require("../assets/img/home-icon6.png"), featureTitle: "Intense integration with Open Source Ecosystem",
            featureContent: "Apache IoTDB (incubating) can support analysis ecosystems, for example, Hadoop, Spark, and Grafana as visualization tool."
          },
        ],
      }
    },
    methods: {
      hover: function (e) {
        e.currentTarget.style.boxShadow = "2px 2px 10px #909090"
      },
      unhover: function (e) {
        e.currentTarget.style.boxShadow = "";
      }
    }
  }

</script>

<style scoped>

  .item{
    margin-bottom: 10px;
  }

  .item > img {
    margin-left: auto;
    margin-top: 5px;
    margin-right: auto;
    width: 95%;
  }
  .carousel-indicators{
    bottom: 0px;
  }

  @media (min-width: 200px) {
    .carousel-inner{
      min-height: 530px;
    }

  }

  @media (min-width: 768px) {
    .feature-item{
      min-height: 200px;
    }
    .carousel-inner{
      min-height: 520px;
    }
  }

  @media (min-width: 992px) {
    .feature-item{
      min-height: 220px;
    }
    .carousel-inner{
      min-height: 580px;
    }
  }

  @media (min-width: 1200px){
    .feature-item{
      min-height: 195px;
    }
    .carousel-inner{
      min-height: 650px;
    }
  }

  .feature-item{
    padding-top: 15px;
    margin-bottom: 10px;
  }
  .main > div {
    margin-top: 10px;
  }

  .home-tittle {
    color: #ffa500;
    font-size: x-large;
    font-weight: 600;
  }

  .feature {
    display: table;
  }

  .Scenarios {
    padding: 5px 10px;
    color: white;
    margin-left: 10px;
    margin-right: 10px;
  }

  .carousel-indicators > li, .carousel-indicators > .active {
    height: 3px;
    width: 30px;
    border-radius: 0px;
    margin: 0px;
    border: none;
  }

  .carousel-indicators > li {
    background-color: rgba(255, 255, 255, .5);
  }

  .carousel-indicators > .active {
    background-color: white;
  }

  .feature > .col-xs-4 > img {
    width: 50px;
    height: 50px;
    margin: 0 8px 8px 0;
  }

  hr {
    position: absolute;
    bottom: 0;
    left: 10px;
    right: 10px;
    margin: 0;
  }

  .row > div > img {
    width: 40px;
    height: 40px;
    margin-left: 3px;
  }

  .feature-title > p {
    font-size: medium;
    margin-left: 5px;
    margin-bottom: 0;
  }

  .feature-content {
    margin-top: 5px;
  }

  article {
    text-align: justify;
  }

  article p {
    font-size: 16px;
    -webkit-hyphens: auto;
    -moz-hyphens: auto;
    -ms-hyphens: auto;
    hyphens: auto;
  }

  .feature-item p {
    font-size: 14px;
  }

  .Scenarios > article > p {
    font-size: 14px;
  }

  .Scenarios > h1 {
    margin-top: 0;
    font-size: 30px;
    color: #fcac45;
  }

</style>
