<template>
    <div class="center">
        <div class="weatcher-block">
            <div class="items">
                <div class="item" v-for="weather_data in weathers" :key="weather_data">
                    <div class="column">

                        <div class="row jc-space-b">
                            <div class="column center-v">
                                <p class="temp">{{ weather_data.temp }}°</p>
                            </div>
                            
                            <img class="weather-ico" :src="`/${ weather_data.desc }.svg`" alt="" srcset="">
                        </div>
                        <div class="row">
                            <p class="temp-other">H:{{ weather_data.temp_max }}°  L:{{ weather_data.temp_min }}°</p>
                        </div>
                        <div class="row jc-space-b">
                            <p class="city-item">
                                {{ weather_data.cityName }}
                            </p>
                            <p class="city-item">
                                {{ weather_data.time }}
                            </p>
                        </div>
                    </div>
                </div>

            </div>
            
            <nuxt-link to="/">
                <div class="back-btn">
                    Вернуть назад
                </div>
            </nuxt-link>
        </div>
    </div>
</template>


<script>
export default {
    setup() {
        
    },

    props: {
        weathers: {
            type: Array,
            default: [],
            required: true
        },
    },
}
</script>