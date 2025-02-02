<script>
  const tarefasAFazer = $state([]);
  const tarefasConcluidas = $state([]);
  let novaTarefa = $state('');
  let tarefaEditadaIndice = $state();
  let tarefaEditadaItem = $state();

  function adicionarTarefa() {
    tarefasAFazer.push(novaTarefa);
    novaTarefa = '';
  }

  function excluirTarefa(i, lista) {
    lista.splice(i, 1);
  }

  function editarTarefa(tarefa, i) {
    tarefaEditadaItem = tarefa;
    tarefaEditadaIndice = i;
  }

  function salvarTarefa(i) {
    if (i < tarefasAFazer.length) {
      tarefasAFazer[i] = tarefaEditadaItem;
    } else {
      tarefasConcluidas[i - tarefasAFazer.length] = tarefaEditadaItem;
    }
    tarefaEditadaItem = '';
    tarefaEditadaIndice = null;
  }

  function marcarConcluida(i) {
    tarefasConcluidas.push(tarefasAFazer[i]);
    tarefasAFazer.splice(i, 1);
  }

  function desmarcarConcluida(i) {
    tarefasAFazer.push(tarefasConcluidas[i]);
    tarefasConcluidas.splice(i, 1);
  }
</script>

<head>
  <style>
    body {
      background-image: url('https://wallpapers.com/images/hd/1920x1080-full-hd-nature-clear-lake-and-flowers-5et15sh9gemfv0jt.jpg');
      background-size: cover;
      background-position: center;
      background-attachment: fixed;
    }

    .container {
  background-color: rgba(0, 0, 0, 0.7); 
  padding: 25px; 
  border-radius: 5px; 
  color: pink
    }
    </style>
</head>

<br><br>

<div class="container">
<center>
  <h2>Tarefas</h2>
  <p>
    <input placeholder="Digite aqui tua nova tarefa..." bind:value={novaTarefa} />
    <button onclick={adicionarTarefa}>+</button>
  </p>

  <h3>Tarefas a Fazer</h3>
  <ul>
    {#each tarefasAFazer as tarefa, i}
      <li>
        {#if tarefaEditadaIndice == i}
          <input bind:value={tarefaEditadaItem} />
          <button class="botao" onclick={() => salvarTarefa(i)}>Salvar</button>
        {:else}
          {tarefa}
          <button class="botao" onclick={() => editarTarefa(tarefa, i)}>Editar</button>
        {/if}
        <button class="botao" onclick={() => excluirTarefa(i, tarefasAFazer)}>Excluir</button>
        <button class="botao" onclick={() => marcarConcluida(i)}>Concluir</button>
      </li>
    {/each}
  </ul>

  <h3>Tarefas Concluídas</h3>
  <ul>
    {#each tarefasConcluidas as tarefa, i}
      <li>
        {#if tarefaEditadaIndice == i + tarefasAFazer.length}
          <input bind:value={tarefaEditadaItem} />
          <button class="botao" onclick={() => salvarTarefa(i + tarefasAFazer.length)}>Salvar</button>
        {:else}
          {tarefa}
          <button class="botao" onclick={() => editarTarefa(tarefa, i + tarefasAFazer.length)}>Editar</button>
        {/if}
        <button class="botao" onclick={() => excluirTarefa(i, tarefasConcluidas)}>Excluir</button>
        <button class="botao" onclick={() => desmarcarConcluida(i)}>Retornar</button>
      </li>
    {/each}
  </ul>

</center></div>
