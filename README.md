# Java-Script-app-Verificador-de-idade
App web Verificador de idade

1ª parte HTML5

2ª parte CSS3

3ª parte JS

Copie e cole os códigos no seu VS Code de preferência e teste no seu navegador.

Imagens para web estão colocadas acima, é só baixar e testar!

<!DOCTYPE html>
<html lang="pt-br">

<head>
    <title>Verificador de idade</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link href="estilo.css" rel="stylesheet">
</head>

<body>
    <header>
        <h1>Verificador de idade</h1>
    </header>
    <section>
        <div>
            <p>Ano de nascimento:
                <input type="number" name="txtano" id="txtano" min="0">
            </p>
            <p>Sexo:
                <input type="radio" name="radsex" id="mas" checked>
                <label for="mas">Masculino</label>
                <input type="radio" name="radsex" id="fem">
                <label for="fem">Feminino</label>
            </p>
            <p>
                <input type="button" value="Verificar" onclick="verificar()">
            </p>
        </div>
        <div id="res">
            Preencha os dados acima para ver o resultado!
        </div>
    </section>
    <footer>
        <p>&copy; Developer Nicole Bidigaray</p>
    </footer>

    <script src="script.js"></script>

</body>

</html>

body {
    background: rgb(70, 142, 236);
    font: normal 15pt Arial;
}

header {
    color: white;
    text-align: center;
}

section {
    background: white;
    border-radius: 10px;
    padding: 15px;
    width: 500px;
    margin: auto;
    box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.363);
}

div {
    padding: 8px;
}

footer {
    color: white;
    text-align: center;
    font-style: italic;
}

function verificar() {
    var data = new Date()
    var ano = data.getFullYear()
    var fano = document.getElementById('txtano')
    var res = document.querySelector('div#res')
    if (fano.value.lenght == 0 || Number(fano.value) > ano) {
        window.alert('[ERRO] Verifique os dados e tente novamente!')
    } else {
        var fsex = document.getElementsByName('radsex')
        var idade = ano - Number(fano.value)
        var gênero = ''
        var img = document.createElement('img')
        img.setAttribute('id', 'foto')
        if (fsex[0].checked) {
            gênero = 'Homem'
            if (idade >= 0 && idade < 5) {
                //Bebê
                img.setAttribute('src', 'bebe-m.png')
            } else if (idade < 15) {
                //Criança
                img.setAttribute('src', 'crianca-m.png')
            } else if (idade > 15 && idade <= 21) {
                //Jovem
                img.setAttribute('src', 'jovem-m.png')
            } else if (idade > 21 && idade <= 50) {
                //Adulto
                img.setAttribute('src', 'adulto-m.png')
            } else {
                //Idoso
                img.setAttribute('src', 'idoso-m.png')
            }
        } else if (fsex[1].checked) {
            gênero = 'Mulher'
            if (idade >= 0 && idade < 5) {
                //Bebê
                img.setAttribute('src', 'bebe-f.png')
            } else if (idade < 15) {
                //Criança
                img.setAttribute('src', 'crianca-f.png')
            } else if (idade > 15 && idade <= 21) {
                //Jovem
                img.setAttribute('src', 'jovem-f.png')
            } else if (idade > 21 && idade <= 50) {
                //Adulto
                img.setAttribute('src', 'adulto-f.png')
            } else {
                //Idoso
                img.setAttribute('src', 'idoso-f.png')
            }
        }
        res.style.textAlign = 'center'
        res.innerHTML = `Detectamos ${gênero} com ${idade} anos.`
        res.appendChild(img)
    }

}
