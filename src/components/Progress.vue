<template>
  <div>
    <h1>{{ title }}</h1>
    <div class="progress"  v-for="(pt, index) in progressType" v-bind:key="index">
      <div class="progress-year">
        <h5 v-bind:style = "{'color': typeColor}">{{ pt.type }} : {{ pt.typeName }}</h5>
        <div class="progress-year-bar">
          <div class="progress-year-bar__passed" v-bind:style = "{'background': pt.progressColor, 'width': pt.progressPercent}"></div>
        </div>
        <div class="progress-year-number">
          {{ pt.progressPercent }}
        </div>
      </div>
    </div>
    <div class="footer">
      <small>©2022 @teohiho</small>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  el: ".progress-bar",
  data() {
    return {
      title: "Progress Bar",
      typeColor: '#858585',
      progressType: [
        {type: "Year Progress", typeName:"", progressColor: "#2795c3", progressPercent: '60%'},
        {type: "Month Progress", typeName:"", progressColor: "#ec407a", progressPercent: '40%'}
      ]
    }
  },
  mounted() {
    this.progressYear(),
    this.progressMonth()
  },
  methods : {
    progressYear: function(){
      let now = new Date();
      let start = new Date(now.getFullYear(), 0, 1);  // Start of this year
      let end = new Date(now.getFullYear() + 1, 0, 1);  // End of this year
      let done = (now-start) / (end-start);
      let percentStr = (100.0 * done).toString();
      if (done < 0.1) {
        percentStr = percentStr.slice(0, 9);
      } else {
        percentStr = percentStr.slice(0, 10);
      }
      
      // show year progress
      let self = this;
      const update_date_interval_time = 50;
      setInterval(function(){
        self.progressType[0].progressPercent = self.progressYear() + "%";
        self.progressType[0].typeName = now.getFullYear();
      }, update_date_interval_time);

      //this.progressType[0].progressPercent = percentStr + "%";

      return percentStr;
    },

    progressMonth: function(){
      let now = new Date();
      let start = new Date(now.getFullYear(), now.getMonth(), 1)  // Start of this month
      let end = new Date(now.getFullYear(), now.getMonth() + 1, 0);  // End of this month
      let done = (now-start) / (end-start);
      let percentStr = (100.0 * done).toString();
      if (done < 0.1) {
        percentStr = percentStr.slice(0, 9);
      } else {
        percentStr = percentStr.slice(0, 10);
      }

      // show month progress
      let self = this;
      const update_date_interval_time = 50;
      const monthNames = ["January", "February", "March", "April", "May", "June",
        "July", "August", "September", "October", "November", "December"
      ];
     
      //this.progressType[1].progressPercent = percentStr + "%";
      //this.progressType[1].typeName = monthNames[now.getMonth()];
      setInterval(function(){
        self.progressType[1].progressPercent = percentStr + "%";
        self.progressType[1].typeName = monthNames[now.getMonth()]
      }, update_date_interval_time);

      return percentStr;
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.progress {
  padding: 10px 30px 10px 30px;
 
}
.progress-year-bar {
  width: 440px;
  padding: 0px;
  background: #f3f3f3;
  box-shadow: 3px 3px 30px 3px rgba(0,0,0,0.1);
  overflow: hidden;
  float:left;
}
.progress-year-bar__passed{
  float:left;
  padding: 5px
}
.progress-year-number{
  width: 165px;
  float:right;
  padding-left: 20px;
}
.footer {
  margin-top: 5vh;
}

</style>
