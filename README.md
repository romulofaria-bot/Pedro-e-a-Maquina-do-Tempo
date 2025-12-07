# Pedro-e-a-Maquina-do-Tempo
Pedro e a Máquina do tempo
<!--
Projeto: Máquina do Tempo - história interativa
Arquivo: index.html
Descrição: Uma página HTML + JavaScript simples e fácil que conta a história de um menino que encontra uma máquina do tempo
Como usar:
1. Salve este arquivo como index.html
2. Coloque-o em um repositório no GitHub (ex.: repo "maquina-do-tempo")
3. Ative GitHub Pages nas configurações do repositório para publicar como site estático (ou abra o arquivo localmente no navegador)

Você pode editar os textos nas seções "events" e nas descrições para adicionar mais aventuras.
-->

<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Máquina do Tempo - Aventura</title>
  <style>
    body{font-family: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial; background: linear-gradient(#f7f9fc,#eef6ff); color:#0b2340; padding:20px}
    .card{max-width:760px;margin:20px auto;padding:18px;border-radius:12px;box-shadow:0 6px 20px rgba(11,35,64,0.08);background:white}
    h1{margin:0 0 8px}
    p.lead{margin-top:6px;color:#3b556e}
    .choices{display:flex;gap:8px;flex-wrap:wrap;margin-top:12px}
    button{padding:10px 14px;border-radius:8px;border:0;background:#0b6cff;color:white;cursor:pointer}
    button.secondary{background:#4a90e2}
    .history{margin-top:14px;padding:12px;border-radius:8px;background:#f5f9ff}
    .small{font-size:0.9rem;color:#3b556e}
    footer{font-size:0.85rem;color:#6b7b8f;margin-top:12px;text-align:center}
  </style>
</head>
<body>
  <div class="card">
    <h1>Pedro e a Máquina do Tempo</h1>
    <p class="lead">Pedro e seus amigos encontraram uma máquina do tempo perdida enquanto brincavam no quintal. Ao ligar a máquina, eles viajaram por diferentes momentos da história do Brasil. Escolha para onde eles vão!</p>

    <div id="story">
      <div class="history" id="intro">
        <strong>Introdução</strong>
        <p>Você é o narrador. Ajude Pedro a escolher um destino. Clique em um evento histórico para levá-lo até lá — cada escolha mostra uma breve cena e uma curiosidade.</p>
      </div>

      <div class="choices">
        <button onclick="visit('1500')">Descobrimento (1500)</button>
        <button onclick="visit('1822')" class="secondary">Independência (1822)</button>
        <button onclick="visit('1888')">Abolição da Escravatura (1888)</button>
        <button onclick="visit('1889')" class="secondary">Proclamação da República (1889)</button>
        <button onclick="visit('1960')">Inauguração de Brasília (1960)</button>
      </div>

      <div class="history" id="scene"></div>

      <div class="history small" id="curiosity"></div>

      <div style="margin-top:12px">
        <button onclick="resetStory()" class="secondary">Voltar</button>
      </div>
    </div>

    <footer>Projeto simples para GitHub — exporte este arquivo como <code>index.html</code> e publique com GitHub Pages.</footer>
  </div>

<script>
  const events = {
    '1500': {
      title: 'Descobrimento do Brasil (1500)',
      scene: `Pedro e os amigos chegam a uma praia grande, veem canoas e indígenas. Eles percebem que o mar e a mata parecem diferentes do que estudaram no colégio. Um navegador estrangeiro observa a costa.`,
      curiosity: 'Curiosidade: Em 22 de abril de 1500, a frota de Pedro Álvares Cabral chegou ao que chamou de "Ilha de Vera Cruz" — hoje sabemos que foi a costa do Brasil.'
    },
    '1822': {
      title: 'Independência do Brasil (1822)',
      scene: `Num campo ensolarado, Pedro encontra gente reunida ouvindo notícias vindas de São Paulo e do Rio. Surge um clima de mudança: pessoas discutem liberdade e o príncipe regente declara que o Brasil será independente.`,
      curiosity: 'Curiosidade: No dia 7 de setembro de 1822, Dom Pedro I declarou a independência do Brasil em um evento celebrado na história como o "Grito do Ipiranga".'
    },
    '1888': {
      title: 'Abolição da Escravatura (1888)',
      scene: `Pedro testemunha um grande ato público em que mulheres e homens celebram uma nova lei. Há emoção no ar: pessoas se abraçam e choram de alegria.`,
      curiosity: 'Curiosidade: A Lei Áurea, assinada em 13 de maio de 1888, aboliu oficialmente a escravidão no Brasil.'
    },
    '1889': {
      title: 'Proclamação da República (1889)',
      scene: `Em praça pública, militares e civis anunciam o fim do regime monárquico. Pedro percebe que a forma de governo está mudando — há energia e apreensão entre as pessoas.`,
      curiosity: 'Curiosidade: Em 15 de novembro de 1889 foi proclamada a República, encerrando a monarquia no Brasil.'
    },
    '1960': {
      title: 'Inauguração de Brasília (1960)',
      scene: `Pedro chega a uma cidade modernista em construção: largos e prédios de formas novas. Arquitetos e trabalhadores estão ocupados, e a capital muda do Rio para um lugar planejado no interior.`,
      curiosity: 'Curiosidade: Brasília foi inaugurada oficialmente em 21 de abril de 1960, projetada por Lúcio Costa e Oscar Niemeyer.'
    }
  };

  function visit(key){
    const ev = events[key];
    if(!ev) return;
    const scene = document.getElementById('scene');
    const curiosity = document.getElementById('curiosity');
    scene.innerHTML = `<strong>${ev.title}</strong><p>${ev.scene}</p>`;
    curiosity.innerHTML = `<strong>Curiosidade</strong><p>${ev.curiosity}</p>`;
    // efeito simples: simular que a máquina temporária "salta" de volta
    flash();
  }

  function flash(){
    const card = document.querySelector('.card');
    card.style.transition = 'transform 0.25s ease, box-shadow 0.25s ease';
    card.style.transform = 'scale(0.995)';
    setTimeout(()=>{card.style.transform = ''},250);
  }

  function resetStory(){
    document.getElementById('scene').innerHTML = '';
    document.getElementById('curiosity').innerHTML = '';
  }
</script>
</body>
</html>
