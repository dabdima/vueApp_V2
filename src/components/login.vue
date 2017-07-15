<template>
    <div id="form">
        <h1>Форма</h1>
        <form action="#" method="post">
            <div class="row">
                <p><label for="label">Логин1</label></p>
                <input type="text" name="login" value="" placeholder="Enter login" size="25" maxlength="30" id="label" />
            </div>
            <div class="row">
                <p><label for="password1">Password</label></p>
                <input type="password" name="password" placeholder="your pass" id="password1" />
            </div>
            <div class="row">
                <p>Оцените наш сайт</p>
                <label><input type="radio" name="avaluation" value="excellent" checked="checked" /> Отлично</label><br />
                <label><input type="radio" name="avaluation" value="good" /> так себе</label><br />
                <label><input type="radio" name="avaluation" value="badly" /> фигня</label><br />
            </div>
            <div class="row">

                <input type="image" name="send" src="send_btn.png" />
            </div>





        </form>
    </div>
</template>

<script>
export default {
  name: 'login',
  data () {
    return {
      msg: 'login'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

    * {
        padding: 0;
        margin: 0;
        text-align: center;
    }

    body {
        font: 12px/1.4 Arial, Verdana, Tahoma, sans-serif;
        color: #5f5f5f;
        background: #b2c8c9;
    }

    #form {
        width: 420px;
        background: #f0f0f0;
        border: 1px solid #a8bcc3;
        margin: 20px auto;
        padding: 20px 40px;
    }

    h1 {
        color: #696969;
        font-size: 18px;
        border-bottom: 1px solid #b6b6b6;
        margin-bottom: 10px;
    }

    .row {
        padding: 5px 0;
    }

    p {
        font-weight: bold;
        margin-bottom: 5px;
        color: #92acb6;
    }

    input[type="text"], input[type="password"], select, textarea {
        font: 12px Arial, Verdana, Tahoma, sans-serif;
        color: #5d5d5d;
        border: 1px solid #b6b6b6;
    }

    input[type="text"], input[type="password"] {
        width: 210px;
        height: 26px;
        padding: 0 5px;
    }

    select {
        width: 210px;
    }

    textarea {
        padding: 5px;
    }

    input[type="image"] {
        margin: 10px 0;
    }
    
</style>
