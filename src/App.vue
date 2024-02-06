<template>
    <div class="wrapper">
        <h1>Погодное приложение</h1>
        <p>Узнать прогноз погоды</p>
        <input type="text" placeholder="введите город" >
        <button>Получить погоду</button>
    </div>
</template>

<script>


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
