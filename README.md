base_dir = "/mnt/data/conilon-site"
os.makedirs(base_dir, exist_ok=True)

index_html = """<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Café Conilon — Guia Completo</title>
  <meta name="description" content="Guia prático sobre o Café Conilon (Coffea canephora): origem, cultivo, diferenças para arábica, preparo e sustentabilidade." />
  <link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 64 64'%3E%3Ctext y='52' x='6' font-size='48'%3E%F0%9F%8D%B5%3C/text%3E%3C/svg%3E">
  <style>
    :root {
      --bg: #0f0f10;
      --card: #151518;
      --muted: #a6a6ad;
      --text: #f1f1f3;
      --brand: #9b6b3d;
      --brand-2: #c8925a;
      --ring: #2a2a31;
      --ok: #5bb98a;
    }
    * { box-sizing: border-box; }
    html, body { margin: 0; padding: 0; background: var(--bg); color: var(--text); font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, Ubuntu, Cantarell, Noto Sans, Helvetica, Arial, "Apple Color Emoji", "Segoe UI Emoji"; }
    a { color: var(--brand-2); text-decoration: none; }
    a:hover { text-decoration: underline; }
    .container { max-width: 1100px; margin: 0 auto; padding: 0 20px; }
    header { position: sticky; top: 0; z-index: 50; backdrop-filter: blur(8px); background: rgba(15,15,16,.7); border-bottom: 1px solid var(--ring); }
    .nav { display: flex; gap: 22px; align-items: center; height: 64px; }
    .brand { display: flex; align-items: center; gap: 10px; font-weight: 700; }
    .bean { width: 28px; height: 28px; display: inline-flex; align-items: center; justify-content: center; border-radius: 8px; background: linear-gradient(135deg, var(--brand), var(--brand-2)); }
    .bean svg { width: 18px; height: 18px; }
    nav a { font-size: 14px; color: var(--muted); padding: 8px 10px; border-radius: 8px; }
    nav a:hover { background: var(--ring); color: var(--text); text-decoration: none; }
    .hero { padding: 72px 0 48px; border-bottom: 1px solid var(--ring); }
    .hero-grid { display: grid; grid-template-columns: 1.3fr .7fr; gap: 28px; align-items: center; }
    .title { font-size: clamp(32px, 7vw, 56px); line-height: 1.05; margin: 0 0 12px; }
    .subtitle { color: var(--muted); font-size: clamp(16px, 2.2vw, 20px); }
    .card { background: linear-gradient(180deg, rgba(255,255,255,.02), rgba(255,255,255,0)); border: 1px solid var(--ring); border-radius: 22px; padding: 22px; box-shadow: 0 20px 60px rgba(0,0,0,.25); }
    .tag { display: inline-block; padding: 6px 10px; border-radius: 999px; background: rgba(155,107,61,.15); color: #ffd7b0; font-size: 12px; border: 1px solid rgba(155,107,61,.35); }
    .cta { display: inline-flex; gap: 10px; align-items: center; padding: 12px 16px; background: linear-gradient(135deg, var(--brand), var(--brand-2)); color: #1a120b; font-weight: 700; border: none; border-radius: 14px; cursor: pointer; margin-top: 16px; }
    .cta:hover { opacity: .95; }
    section { padding: 56px 0; border-bottom: 1px solid var(--ring); }
    h2 { margin: 0 0 18px; font-size: clamp(24px, 4vw, 34px); }
    p { color: #d8d8dc; line-height: 1.65; }
    .grid { display: grid; gap: 18px; }
    .grid-3 { grid-template-columns: repeat(3, 1fr); }
    .grid-2 { grid-template-columns: repeat(2, 1fr); }
    .stat { display: flex; gap: 12px; align-items: center; }
    .stat b { font-size: 22px; }
    .badge { font-size: 12px; color: var(--muted); border: 1px dashed var(--ring); border-radius: 10px; padding: 4px 8px; }
    .list { margin: 10px 0 0 0; padding: 0 0 0 18px; color: #d8d8dc; }
    .faq-item { border: 1px solid var(--ring); border-radius: 16px; padding: 16px; }
    .faq-q { display: flex; justify-content: space-between; cursor: pointer; }
    .faq-a { color: #cfcfd6; display: none; margin-top: 10px; }
    footer { padding: 28px 0; color: var(--muted); }
    .pill { padding: 8px 10px; background: #121216; border: 1px solid var(--ring); border-radius: 999px; display: inline-flex; gap: 8px; align-items: center; }
    .note { font-size: 12px; color: var(--muted); }
    @media (max-width: 900px) {
      .hero-grid, .grid-3, .grid-2 { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>
  <header>
    <div class="container nav">
      <div class="brand">
        <span class="bean" aria-hidden="true">
          <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M12 3c3 0 9 2 9 9s-6 9-9 9-9-2-9-9 6-9 9-9Z" fill="currentColor" opacity=".25"/>
            <path d="M10.5 4C9 6.5 8 9 8 12s1 5.5 2.5 8" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
          </svg>
        </span>
        <span>Café Conilon</span>
      </div>
      <nav style="margin-left:auto; display:flex; gap:10px;">
        <a href="#oque-e">O que é</a>
        <a href="#cultivo">Cultivo</a>
        <a href="#diferencas">Diferenças</a>
        <a href="#preparo">Preparo</a>
        <a href="#sustentabilidade">Sustentabilidade</a>
        <a href="#faq">FAQ</a>
        <a href="#contato">Contato</a>
      </nav>
    </div>
  </header>

  <main>
    <section class="hero">
      <div class="container hero-grid">
        <div>
          <span class="tag">Coffea canephora (robusta)</span>
          <h1 class="title">Tudo sobre o <span style="background:linear-gradient(135deg,var(--brand),var(--brand-2)); -webkit-background-clip:text; color:transparent;">Café Conilon</span></h1>
          <p class="subtitle">Origem, características, manejo no campo e como tirar o máximo no preparo em casa ou na cafeteria.</p>
          <button class="cta" onclick="document.querySelector('#oque-e').scrollIntoView({behavior:'smooth'})">Começar o guia →</button>
          <div style="margin-top:18px; display:flex; gap:12px; flex-wrap:wrap;">
            <span class="pill">☕ Corpo intenso</span>
            <span class="pill">⚡ Mais cafeína</span>
            <span class="pill">🌧️ Resistente ao clima</span>
          </div>
        </div>
        <div class="card">
          <h3 style="margin-top:0;">Resumo rápido</h3>
          <div class="grid grid-2">
            <div class="stat"><b>70–90%</b><span class="note">do conilon é usado em blends</span></div>
            <div class="stat"><b>Baixa acidez</b><span class="note">perfil sensorial típico</span></div>
            <div class="stat"><b>Produtivo</b><span class="note">robusto no campo</span></div>
            <div class="stat"><b>Espresso</b><span class="note">crema densa</span></div>
          </div>
        </div>
      </div>
    </section>

    <section id="oque-e">
      <div class="container grid grid-2">
        <div class="card">
          <h2>O que é Conilon?</h2>
          <p>Conilon é como o Brasil chama o café da espécie <em>Coffea canephora</em>, também conhecido como robusta. Ele se destaca pela <strong>alta produtividade</strong>, <strong>maior teor de cafeína</strong> e <strong>resistência a pragas e clima</strong>. No xícara, costuma ter corpo alto, crema espessa (no espresso) e acidez mais baixa quando comparado ao arábica.</p>
          <p>Estados como Espírito Santo e Rondônia são referências no cultivo, com avanço de qualidade em <strong>colheita seletiva, secagem controlada</strong> e <strong>processamentos</strong> (natural, honey, fermentações dirigidas).</p>
        </div>
        <div class="card">
          <h2>Quando usar</h2>
          <ul class="list">
            <li>Para <strong>blends de espresso</strong> com corpo e crema.</li>
            <li>Em <strong>cafeteira italiana</strong> e métodos de pressão.</li>
            <li>Como base para <strong>bebidas com leite</strong>.</li>
            <li>Single origin de <strong>robusta fino</strong> quando bem processado.</li>
          </ul>
          <p class="note">Dica: moa um pouco mais grosso que arábica no filtro para evitar adstringência.</p>
        </div>
      </div>
    </section>

    <section id="cultivo">
      <div class="container grid grid-3">
        <div class="card">
          <h2>Cultivo & Manejo</h2>
          <p>Conilon prefere <strong>clima quente</strong> e altitudes mais baixas. Tolera melhor a umidade e apresenta <strong>ramificação vigorosa</strong>, exigindo podas de condução e formação de múltiplos caules.</p>
          <ul class="list">
            <li>Espaçamento comum: 3x1&nbsp;m (varia por sistema).</li>
            <li>Adubação nitrogenada e potássica equilibrada.</li>
            <li>Irrigação melhora estabilidade produtiva.</li>
            <li>Colheita quando a maioria dos frutos estiver madura.</li>
          </ul>
        </div>
        <div class="card">
          <h2>Pós-colheita</h2>
          <p>O processamento define muito do perfil: <strong>natural</strong> para doçura e corpo; <strong>honey</strong> para equilíbrio; <strong>lavado</strong> para limpeza. Controle temperatura e fluxo de ar na secagem.</p>
          <ul class="list">
            <li>Secagem até ~11–12% de umidade.</li>
            <li>Fermentações guiadas podem reduzir notas verdes.</li>
          </ul>
        </div>
        <div class="card">
          <h2>Qualidade sensorial</h2>
          <p>Notas típicas incluem <em>cacau, nozes, especiarias</em>. Projetos de robusta fino têm alcançado doçura alta e finalização limpa, ampliando seu uso como <strong>single origin</strong>.</p>
          <div class="badge">Atenção: torra média a média-escura favorece cremosidade.</div>
        </div>
      </div>
    </section>

    <section id="diferencas">
      <div class="container grid grid-2">
        <div class="card">
          <h2>Conilon x Arábica</h2>
          <ul class="list">
            <li><strong>Cafeína</strong>: conilon ~2.2–2.7%; arábica ~1.2–1.8%.</li>
            <li><strong>Óleos & sólidos</strong>: mais altos no conilon → <em>corpo</em>.</li>
            <li><strong>Acidez</strong>: geralmente mais baixa no conilon.</li>
            <li><strong>Produtividade</strong>: maior no conilon.</li>
          </ul>
        </div>
        <div class="card">
          <h2>Quando misturar</h2>
          <p>Blends populares: <strong>70/30</strong> (arábica/conilon) para equilíbrio, ou <strong>50/50</strong> para bebidas com leite. Ajuste a extração para domar amargor.</p>
          <ul class="list">
            <li>Espresso: 92–95 °C, 1:2 em 25–30 s (ponto de partida).</li>
            <li>Italiana: chama baixa, retire assim que “subir”.</li>
          </ul>
        </div>
      </div>
    </section>

    <section id="preparo">
      <div class="container grid grid-3">
        <div class="card">
          <h2>Filtro</h2>
          <p>Proporção 1:15 a 1:16. Moagem <strong>um passo</strong> mais grossa que para arábica. Despejos pulsados reduzem amargor.</p>
        </div>
        <div class="card">
          <h2>Espresso</h2>
          <p>Ótimo para <em>crema</em> densa. Se amargar, reduza temperatura, encurte tempo ou aumente a dose sem compactar demais.</p>
        </div>
        <div class="card">
          <h2>Prensa/Imersão</h2>
          <p>4 minutos, mexa levemente após 1 minuto. Filtre com calma para evitar turbidez excessiva.</p>
        </div>
      </div>
    </section>

    <section id="sustentabilidade">
      <div class="container grid grid-2">
        <div class="card">
          <h2>Sustentabilidade</h2>
          <p>Conilon bem manejado pode <strong>reduzir insumos</strong> pelo vigor da planta. Boas práticas incluem <strong>sombrite parcial</strong>, <strong>adubação orgânica</strong> e <strong>uso racional da água</strong>.</p>
        </div>
        <div class="card">
          <h2>Mercado</h2>
          <p>Demanda crescente por <strong>robusta de qualidade</strong> em cápsulas, solúveis e espressos. Produtores têm investido em <strong>pós-colheita</strong> para valorizar a xícara.</p>
        </div>
      </div>
    </section>

    <section id="faq">
      <div class="container grid">
        <h2>FAQ</h2>
        <div class="faq-item">
          <div class="faq-q" onclick="toggleFaq(this)">
            <strong>Conilon dá mais energia?</strong>
            <span>+</span>
          </div>
          <div class="faq-a">Sim. O conilon costuma ter teor de cafeína mais alto do que o arábica, o que pode resultar em sensação de maior estímulo.</div>
        </div>
        <div class="faq-item">
          <div class="faq-q" onclick="toggleFaq(this)">
            <strong>É sempre mais amargo?</strong>
            <span>+</span>
          </div>
          <div class="faq-a">Não necessariamente. Torra e extração adequadas podem evidenciar doçura e notas de cacau, reduzindo amargor e adstringência.</div>
        </div>
        <div class="faq-item">
          <div class="faq-q" onclick="toggleFaq(this)">
            <strong>Posso usar em café coado?</strong>
            <span>+</span>
          </div>
          <div class="faq-a">Sim! Ajuste a moagem um pouco mais grossa e use proporções 1:15–1:16 para resultados equilibrados.</div>
        </div>
      </div>
    </section>

    <section id="contato">
      <div class="container grid grid-2">
        <div class="card">
          <h2>Fale conosco</h2>
          <p>Tem dúvidas, quer sugerir conteúdo ou parcerias? Envie um e-mail:</p>
          <p class="pill">✉️ contato@seusite.com</p>
          <p class="note">Substitua pelo seu e-mail real ao publicar.</p>
        </div>
        <div class="card">
          <h2>Licença & Créditos</h2>
          <p>Este site é um exemplo educativo, livre para uso e adaptação. Basta manter os créditos.</p>
          <p class="note">© {year} Café Conilon — Guia.</p>
        </div>
      </div>
    </section>
  </main>

  <footer>
    <div class="container" style="display:flex; justify-content:space-between; flex-wrap:wrap; gap:10px;">
      <span>Feito com ☕ e HTML puro.</span>
      <span class="note">Versão 1.0</span>
    </div>
  </footer>

  <script>
    function toggleFaq(el) {
      const ans = el.nextElementSibling;
      const open = ans.style.display === 'block';
      ans.style.display = open ? 'none' : 'block';
      el.querySelector('span').textContent = open ? '+' : '–';
    }
  </script>
</body>
</html>
""".replace("{year}", str(datetime.date.today().year))

# Write files
with open(os.path.join(base_dir, "index.html"), "w", encoding="utf-8") as f:
    f.write(index_html)

# Zip it
zip_path = "/mnt/data/site-cafe-conilon.zip"
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    for root, _, files in os.walk(base_dir):
        for name in files:
            full = os.path.join(root, name)
            rel = os.path.relpath(full, base_dir)
            z.write(full, arcname=os.path.join("conilon-site", rel))

zip_path
