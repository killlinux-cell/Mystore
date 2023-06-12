<template>
    <footer class="footer">
        <div class="footer-left">
            <img src="logo.Png" alt="image_monlogo">
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Repudiandae, vitae. Odio excepturi illum aliquam, incidunt recusandae rerum provident quaerat quia nostrum cupiditate fugit aperiam culpa tempora quisquam quasi ex fuga!</p>
            <div class="socials">
                <a href=""><i class="fa fa-facebook"></i></a>
                <a href=""><i class="fa fa-twitter"></i></a>
                <a href=""><i class="fa fa-dribble"></i></a>
                <a href=""><i class="fa fa-youtube"></i></a>
            </div>
        </div>
        <ul class="footer-right">
            <li>
                <h2>Produits</h2>

                <ul class="box">
                    <li><a href="">Maillot équipe national</a></li>
                    <li><a href="">Maillot Club</a></li>
                    <li><a href="">Maillot Légendaire</a></li>
                    <li><a href="">Chaussure Sport</a></li>
                    <li><a href="">Accessoires</a></li>
                </ul>
            </li>

            <li class="features">
                <h2>Liens utiles</h2>

                <ul class="box">
                    <li><a href="">Fif</a></li>
                    <li><a href="">CDML</a></li>
                    <li><a href="">PepeSoupe</a></li>
                    <li><a href="">NCI</a></li>
                    <li><a href="">CanalBox</a></li>
                </ul>
            </li>

             <li>
                <h2>Adresses</h2>

                <ul class="box">
                    <li><a href="">Abidjan, Marcory 05</a></li>
                    <li><a href="">Quartier Mau</a></li>
                    <li><a href="">Abidjan</a></li>
                    <li><a href="">Côte d'Ivoire</a></li>
                </ul>
            </li>

        </ul>

        <div class="footer-bottom">
            <p>All Right Reserved by &copy;CDML 2023</p>
        </div>
    </footer>
</template>

<script>

export default{
    name: 'FooterView',
}
</script>

<style scoped>

.footer{
    display: -webkit-flex;
    display: -moz-flex;
    display: -ms-flex;
    display: -o-flex;
    display: flex;
    flex-flow: row wrap;
    padding: 50px;
    color: #fff;
    background-color: #011c39;

}

.footer > *{
    flex: 1 100px;
}

.footer-left{
    margin-right: 1.25em;
    margin: 2em;
}

.footer-left img{
    width: 50%;
}

h2{
    font-weight: 400;
    font-size: 17px;
}
.footer ul{
    list-style: none;
    padding-left: 0;
}

.footer li{
    line-height: 2em;
}

.footer a{
    text-decoration: none;
}
.footer-right{
    display: -webkit-flex;
    display: -moz-flex;
    display: -ms-flex;
    display: -o-flex;
    display: flex;
    flex-flow: row wrap;
}

.footer-right > *{
    flex: 1 50%;
    margin-right: 1.25em;
}

.box a{
    color: #999;
}
.footer-bottom{
    text-align: center;
    color: #999;
    padding-top: 50px;
}

.footer-left p{
    padding-right: 20%;
    color: #999;
}

.socials a{
    background: #463a62;
    width: 40px;
    height: 40px;
    display: inline-block;
    margin-right: 10px;
}

.socials a{
    color: #e7f2f4;
    padding: 10px 12px;
    font-size: 20px;
}


@media screen and (min-width: 600px) {
    .footer-right > *{
        flex: 1;
    }
    .footer-left{
        flex: 1 0px;
    }

    .footer-right{
        flex: 2 0px;
    }
}

@media (max-width: 600px) {
    .footer{
        padding: 15px;
    }
} 
</style>