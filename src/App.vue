<template>
    <div class="wrapper">
        <h1>Погодное приложение </h1>
        <p>Узнать прогноз погоды в {{ city === '' ? 'вашем городе' : cityName }}</p>
        <input type="text" v-model="city" placeholder="введите город" >
        <button v-show="city" @click="getWeather()">Получить погоду</button>
        <p class="error"> {{}}</p>
    </div>

    <div v-if="info != null">
        <p>{{ showTemp }}</p>
        <p>{{ showFeelsLike }}</p>
        <p>{{ showMinTemp }}</p>
        <p>{{ showMaxTemp }}</p>
    </div>

</template>

<script>
import axios from 'axios'
export default {

    //храним в data() все переменные с которыми взаимодействуем в этом компоненте
    data() {
        return {
            city: '',
            error: '',
            info: null
        }
    },
    //computed cвойство - это автоматическое обрабатываемое сво-во
    computed: {
        cityName() {
            return "*" + this.city + "*"
        },
        showTemp() {
            return "Температура: " + this.info.main.temp
        },
        showFeelsLike() {
            return "Ощущается как: " + this.info.main.feels_like
        },
        showMinTemp() {
            return "Минимальная температура: " + this.info.main.temp_min
        },
        showMaxTemp() {
            return "Максимальная температура: " + this.info.main.temp_max
        },

    },
    //здесь пишутся методы в methods
    methods: {
        getWeather() {
            //trim() удаляет личшние пробелы до и после
            if(this.city.trim().length < 2) {
                this.error = 'Нужно название более 1 символа';
                return false;
            }

            axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=3d9de74844d28377e81415151cbe6a66`)
                .then(res => (this.info = res.data))

        }
    }
}

</script>

<style>
.wrapper {
    width: 900px;
    height: 500px;
    border-radius: 50px;
    background: rgb(45, 45, 84);
    padding: 20px;
    text-align: center;
    color: #fcfcfc;
}

.wrapper h1 {
    margin-top: 50px;
}

.wrapper p {
    margin-top: 20px;
}

.wrapper input {
    margin-top: 30px;
    background-color: transparent;
    border: 0;
    border-bottom: 2px solid #110813;
    color: #fcfcfc;
    font-size: 14px;
    padding: 5px 8px;
    outline: none;

}

.wrapper input:focus{
    border-bottom-color: #feecf7;
}

.wrapper button {
    background: #e1cc45;
    color: #fcfcfc;
    border-radius: 10px;
    border: 2px solid #ffc107;
    padding: 10px 15px;
    margin-left: 20px;
    cursor:pointer;
    transition: transform 500ms ease;
}

.wrapper button:hover {
    transform: scale(1.1) translateY(-5px);
}
</style>
