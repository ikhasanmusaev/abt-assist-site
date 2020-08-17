<template>
    <div id="AppFooter">
        <h2>Contact</h2>
        <div class="contact">
            <div class="app_link">
                <a href=""><img src="../assets/img/icon-g-p.png" alt="Icon"></a>
                <span><a href=""> Ilovani bepul yuklab olish <br> uchun shu yerga bosing! </a> </span>
            </div>
            <div class="contact-form">
                <form action="">
                    <label>
                        <input type="text" placeholder="Ismingiz">
                    </label>
                    <label>
                        <input type="text" placeholder="Emalingiz">
                    </label>
                    <label for="comment"></label>
                    <textarea name="comment" id="comment" cols="30" rows="10"
                              placeholder="Xabar matni"/>
                    <button>Yuborish</button>
                </form>
            </div>
            <div class="contact-info">
                <div class="contact-info__text">
                    Savol, taklif, shikoyat va <br>
                    arizalaringiz uchun,<br>
                    biz bilan bog‘lanishingiz <br>
                    mumkin.
                </div>
                <div class="contact-infos">
                    <img src="../assets/img/tel-icon.png" alt="tel-icon">
                    <span>
                        Tel: +9989X XXX XX XX
                    </span>
                </div>
                <div class="contact-infos">
                    <img src="../assets/img/mail-icon.png" alt="email-icon">
                    <span>
                        hashcolonteam@gmail.com
                    </span>
                </div>
            </div>
        </div>
        <div class="team">
            <p>
                #:TEAM - 2020
            </p>
        </div>
    </div>
</template>

<script>
    export default {
        name: "AppFooter"
    }
</script>

<style scoped>
    #AppFooter {
        display: flex;
        flex-direction: column;
        background: #51C75B;
        border-top: 4px solid #0029FF;
        box-shadow: 0 4px 100px rgba(0, 0, 0, 0.5);
    }

    h2 {
        color: #FFFFFF;
        text-align: center;
    }

    .contact {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-items: center;
        justify-content: center;

        font-style: normal;
        font-weight: bold;
        font-size: 22px;
        line-height: 26px;
        color: #FFFFFF;
    }

    .contact-form {
        width: 33%;
    }

    .contact-form input {
        width: 404px;
        height: 35px;
        border-radius: 7px;
        border: none;
        margin: 10px 0;
        padding: 8px;
        font-size: 18px;
    }

    .contact-form textarea {
        width: 404px;
        height: 107px;
        border: none;
        resize: none;
        margin: 10px 0;
        border-radius: 7px;
        padding: 8px;
        font-size: 18px;
    }

    .contact-form button {
        background: #FFFFFF;
        color: #51C75B;
        border: none;
        margin: 10px 0;
        font-size: 18px;
        font-weight: bold;
        border-radius: 5px;
        height: 40px;
        width: 40%;
        cursor: pointer;
    }

    .app_link {
        display: block;
        width: 33%;
    }

    .app_link span {
        margin-top: 15px;
        display: block;
        margin-left: 80px;
    }

    .app_link img {
        height: 50px;
        margin-left: 80px;
    }

    .app_link a {
        color: #FFFFFF;
        text-decoration: none;
    }

    .contact-form form {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .contact-info {
        width: 33%;
    }

    .contact-info__text {
        margin-left: 80px;
    }

    .contact-infos {
        display: flex;
        justify-items: center;
        margin: 15px 0 15px 80px;
    }

    .contact-infos span {
        margin-left: 10px;
    }

    .team {
        background: #ffffff;
        height: 20px;
        width: 100%;
        margin-bottom: 20px;
    }

    .team p {
        margin: 0 8px 0 auto;
        padding: 0;
        height: 100%;
        color: #51C75B;
        font-size: 16px;
        font-weight: bold;
        float: right;
    }

</style>