<template>
	
	<div>
		<Weather :weathers="weather" />
	</div>
</template>

<script>
export default {
	async asyncData({ params }) {
		// передаем cityName из $route.params.id
		const weather = await getWeather(params.id);
		return { weather };
	},
};


async function getWeather(cityName) {
    const url = `https://api.openweathermap.org/data/2.5/forecast?q=${cityName}&cnt=6&appid=c0339275f7f4f40a5e289951063fd1a1&units=metric&lang=ru`;

    const response = await fetch(url);
    const weatherList = [];

    if (response.status === 200) {
        const data = await response.json();
        for (let forecast of data.list) {
            const tempCelsius = forecast.main.temp;
            const forecastTime = String(new Date(forecast.dt * 1000).toLocaleString('en-US', {day: 'numeric', month: 'short', year: 'numeric', hour: '2-digit', minute: '2-digit'}));

            weatherList.push(
				{
					cityName,
					time: forecastTime,
					temp: Math.floor(tempCelsius),
					temp_max: forecast.main.temp_max,
					temp_min: forecast.main.temp_max,
					desc: forecast.weather[0].main,
				}
			);
        }

        return weatherList;
    } else {
        console.log('An error occurred while retrieving weather data.');
    }  
}  
</script>

