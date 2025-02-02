<svelte:head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Bem-vindo</title>
    <link
        href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css"
        rel="stylesheet"
    />
</svelte:head>

<div class="pagina">
    <div class="d-flex justify-content-center align-items-center min-vh-100">
        <div class="text-center">
            <h1 class="fonte">Seja muito Bem-Vindo ao meu site</h1>
            
            <div class="info-container bg-dark bg-opacity-75 p-4 rounded-3">
                <h3 class="mb-3">Sobre o Site:</h3>
                Muito bem! Aqui nesse site vou falar um pouco sobre dieta, nutrientes e metabolismo, espero que goste! <br>
                O site foi feito utilizando a base do site que já estavamos fazendo em sala de aula;
            </div>
        </div>
    </div>
</div>

<style>
    .pagina {
        background-image: url('https://images2.alphacoders.com/127/1271121.jpg');
        background-size: cover;
        background-position: center;
        background-attachment: fixed;
        min-height: 100vh;
        color: white;
    }

    .info-container {
        background-color: rgba(0, 0, 0, 0.5);
        backdrop-filter: blur(5px);
        max-width: 600px;
        margin: 0 auto;
    }

    .fonte{
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        font-weight: 700;
    }
</style>
