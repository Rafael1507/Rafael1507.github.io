<script>
  let celsius = 0,
    lunitemp = 0;

  function c2f() {
    lunitemp = (celsius - 10) / 2.5;
  }

  function f2c() {
    celsius = lunitemp * 2.5 + 10;
  }
</script>

<head>
  <style>
    body {
      background-image: url('https://media.istockphoto.com/id/1323823418/pt/foto/low-angle-view-thermometer-on-blue-sky-with-sun-shining.jpg?s=612x612&w=0&k=20&c=84-6TeESz1sfxMCa_XdW-pB64tUkZ4rQ2O0e-6FfzH8=');
      background-size: cover;
      background-position: center;
      background-attachment: fixed;
      height: 100vh;
    }

    .content-container {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 5vh;
    }

    / .container {
      background-color: rgba(9, 1, 1, 0.5);
      padding: 40px;
      border-radius: 282px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
      color: #3333;
    }
    .content-batata1 {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 10vh;
    }
    .batata1 {
      background-color: rgba(9, 1, 1, 0.5);
      padding: 50px;
      border-radius: 50px;
      color: #00000;
    }
  </style>
</head>
<body>
  <div class="content-container">
    <div class="container">
      <h1 class="text-center">Temperatura</h1>
    </div>
  </div>
</body>

<div class="content-batata1">
  <div class="batata1">
    <h1 class="text-left">Celsius:</h1>
    <h3><input oninput={c2f} type="number" bind:value={celsius} /></h3>

    <h1 class="text-left">Lunitemp:</h1>
    <h3><input oninput={f2c} type="number" bind:value={lunitemp} /></h3>
  </div>
</div>
