<template>
    <div class="center">
        <div class="cities">
            <nuxt-link :to="'/weather/' + city" v-for="city in cities" :key="city">
                <div class="city">
                    {{ city }}
                </div>
            </nuxt-link>
        </div>
    </div>
</template>


<script>
export default {
    setup() {
        return {
            cities: [
                "Москва",
                "Подольск",
                "Санкт-Петербург",
                "Калининград",
                "Тюмень",
                "Сочи",
                "Нижний Новгород",
                "Казань",
                "Екатеринбург",
            ]
        }
    },
}
</script>