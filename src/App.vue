<template>
<div class="m-auto">
  <div class="flex">
  <h1 class="2xl text-center">Count down </h1>
  <p>
      {{ days }} days,
    {{ hours }} hours, {{ minutes }} minute, {{ seconds }} seconds
    
    
  </p>
  </div>
  </div>
</template>

<script>

export default {
  name: "App",
  data() {
    return {
        endate: new Date("Jun 28, 2022 10:00:00").getTime(),
        interval:"",
        days:"",
        hours:"",
        minutes:"",
        seconds:"",
    };
  },
  methods:{
        /**
         * Method to get the number of days to countdown
         */
        getDays(){
            return Math.floor(this.interval / (1000 * 60 * 60 * 24))
        },
     
        /**
         * Method to get the number of hour to countdown
         */
        gethours(){
             return Math.floor((this.interval % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
        },
        
        
        /**
         * Method to get the number of days to countdown
         */
        getMinutes(){
            return Math.floor((this.interval % (1000 * 60 * 60  )) / (1000 * 60))
        },

       
        /**
         * Method to get the number of days to countdown
         */
        getseconds(){
            return Math.floor((this.interval % (1000 * 60 )) / (1000))
        },

       startCountdown() {
            this.funcInterval = setInterval(() => {
                let dateTo = new Date().getTime()
                this.interval = this.endate - dateTo
                this.days = this.getDays()
                this.hours = this.gethours()
                this.minutes = this.getMinutes()
                this.seconds = this.getseconds()

       })
  },
},
 mounted () {
        this.startCountdown();
    },
}

</script>