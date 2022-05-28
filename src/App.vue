<template>
<h1 class="5xl text-center font-bold">Count down to 50 days of Vue </h1>
<div class="m-auto flex my-10 justify-center">

  
  <div class="h-20 w-20 md:h-24 md:w-24 border rounded opacity-50 bg-pink-100 flex justify-center items-center">
      <Span class="text-5xl font-black">{{days}}</Span>
    </div>
        <div class="h-20 w-20 md:h-24 md:w-24 border rounded opacity-50 bg-pink-100 flex justify-center items-center">
          <Span class="text-5xl font-black">{{hours}}</Span>
        </div>
        <div class="h-20 w-20 md:h-24 md:w-24 border rounded opacity-50 bg-pink-100 flex justify-center items-center">
          <Span class="text-5xl font-black">{{minutes}}</Span>
        </div>
          <div class="h-20 w-20 md:h-24 md:w-24 border rounded opacity-50 bg-pink-100 flex justify-center items-center">
            <Span class="text-5xl font-black">{{seconds}}</Span>
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
         * Method to get the number of hours to countdown
         */
        gethours(){
             return Math.floor((this.interval % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
        },
        
        
        /**
         * Method to get the number of minutes to countdown
         */
        getMinutes(){
            return Math.floor((this.interval % (1000 * 60 * 60  )) / (1000 * 60))
        },

       
        /**
         * Method to get the number of seconds to countdown
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