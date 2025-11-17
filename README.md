<!DOCTYPE html>:root {// Menu mobile
const toggle = document.getElementById('menuToggle');
const menu = document.getElementById('menu');
toggle?.addEventListener('click', () => {
  const open = menu.style.display === 'flex';
  menu.style.display = open ? 'none' : 'flex';
});

// Ano automático no rodapé
document.getElementById('year').textContent = new Date().getFullYear();

// Simulação de envio do formulário
const form = document.getElementById('formOrcamento');
const statusEl = document.getElementById('formStatus');

form?.addEventListener('submit', async (e) => {
  e.preventDefault();
  statusEl.textContent = 'Enviando...';
  statusEl.style.color = '#38bdf8';

  // Coleta dos dados
  const data = Object.fromEntries(new FormData(form).entries());

  // Exemplo: envio via WhatsApp (abre conversa com os dados)
  const msg = encodeURIComponent(
    `Olá! Novo orçamento:\n` +
    `Nome: ${data.nome}\nTelefone: ${data.telefone}\n` +
    `Cidade: ${data.cidade}\nServiço: ${data.servico}\n` +
    `Descrição: ${data.descricao}\nPreferência: ${data.preferencia}`
  );
  const wa = `https://wa.me/5598SEUNUMERO?text=${msg}`;
  window.open(wa, '_blank');

  // Feedback
  setTimeout(() => {
    statusEl.textContent = 'Pronto! Abrimos o WhatsApp com seu orçamento.';
    statusEl.style.color = '#22c55e';
    form.reset();
  }, 600);
});
  --bg: #0f172a;
  --card: #111827;
  --text: #e5e7eb;
  --muted: #9ca3af;
  --primary: #22c55e;
  --primary-700: #16a34a;
  --accent: #38bdf8;
  --white: #ffffff;
}

* { box-sizing: border-box }
html, body { margin: 0; padding: 0; }
body {
  font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, sans-serif;
  color: var(--text);
  background: linear-gradient(180deg, #0b1220, var(--bg));
}

img { max-width: 100%; display: block; border-radius: 10px; }

.container {
  width: 100%;
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 20px;
}

/* Header */
.header { position: sticky; top: 0; z-index: 50; background: rgba(15,23,42,0.8); backdrop-filter: blur(8px); border-bottom: 1px solid #1f2937; }
.nav { display: flex; align-items: center; justify-content: space-between; height: 64px; }
.logo { font-weight: 800; color: var(--white); text-decoration: none; letter-spacing: 0.2px; }
.logo span { color: var(--accent); }
.menu a { color: var(--text); text-decoration: none; margin: 0 14px; font-weight: 600; }
.menu a:hover { color: var(--accent); }
.btn { background: var(--primary); color: var(--bg); padding: 12px 18px; border-radius: 10px; text-decoration: none; font-weight: 700; display: inline-block; border: 0; cursor: pointer; }
.btn:hover { background: var(--primary-700); }
.btn-outline { background: transparent; color: var(--text); border: 2px solid var(--accent); }
.btn-sm { padding: 8px 12px; }

.menu-toggle { display: none; background: transparent; color: var(--text); border: 0; font-size: 24px; }

/* Hero */
.hero { padding: 60px 0; }
.hero-grid { display: grid; grid-template-columns: 1.2fr 1fr; gap: 32px; align-items: center; }
.hero-text h1 { font-size: 36px; line-height: 1.15; margin: 0 0 10px; }
.hero-text p { color: var(--muted); margin: 0 0 16px; }
.hero-actions { display: flex; gap: 12px; margin: 16px 0 8px; }
.selos { display: flex; gap: 12px; list-style: none; padding: 0; margin: 10px 0 0; color: var(--accent); font-weight: 700; }

/* Sections */
.section { padding: 60px 0; }
.section.alt { background: #0c1426; border-top: 1px solid #172031; border-bottom: 1px solid #172031; }
.section h2 { font-size: 28px; margin: 0 0 8px; }
.section p { color: var(--muted); }

/* Cards */
.cards { display: grid; grid-template-columns: repeat(4, 1fr); gap: 18px; margin-top: 20px; }
.card { background: var(--card); padding: 16px; border-radius: 14px; border: 1px solid #1f2937; }
.card h3 { margin: 12px 0 6px; }
.card p { color: var(--muted); }

.grid.two { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; }

/* Gallery */
.gallery { grid-template-columns: repeat(3, 1fr); gap: 12px; }
.gallery img { height: 220px; object-fit: cover; }

/* Testimonials */
.testimonials { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; }
blockquote { background: var(--card); border: 1px solid #1f2937; padding: 16px; border-radius: 12px; }
blockquote footer { color: var(--muted); margin-top: 8px; }

/* About */
.about { display: grid; grid-template-columns: 1.2fr 1fr; gap: 20px; }
.about-img img { height: 100%; object-fit: cover; }

/* Form */
.form { background: var(--card); border: 1px solid #1f2937; border-radius: 14px; padding: 18px; margin-top: 16px; }
label span { display: block; margin-bottom: 6px; font-weight: 600; }
input, select, textarea {
  width: 100%; padding: 12px; border-radius: 10px; border: 1px solid #334155; background: #0b1220; color: var(--text);
}
.form-status { margin-top: 12px; color: var(--accent); font-weight: 600; }

/* Contact */
.contact { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; align-items: start; }
.contact-list { list-style: none; padding: 0; }
.contact-list li { margin: 6px 0; }
.social { display: flex; gap: 12px; margin-top: 10px; }
.map iframe { width: 100%; min-height: 260px; border: 0; border-radius: 12px; background: #0b1220; }

/* Footer */
.footer { padding: 24px 0 60px; background: #0b1220; border-top: 1px solid #172031; }
.footer-grid { display: grid; grid-template-columns: 1fr 1fr; align-items: start; }
.footer-logo { display: inline-block; margin-bottom: 8px; }
.footer-links { display: grid; grid-template-columns: repeat(3, auto); gap: 8px 16px; list-style: none; padding: 0; }
.whatsapp-float {
  position: fixed; right: 18px; bottom: 18px; width: 52px; height: 52px; display: grid; place-items: center;
  background: #25D366; color: #042b1a; border-radius: 50%; text-decoration: none; font-size: 22px; box-shadow: 0 8px 20px rgba(0,0,0,0.3);
}

/* Responsive */
@media (max-width: 980px) {
  .hero-grid, .cards, .gallery, .testimonials, .about, .contact, .footer-grid { grid-template-columns: 1fr; }
  .grid.two { grid-template-columns: 1fr; }
  .menu { display: none; flex-direction: column; gap: 12px; padding: 16px; background: #0b1220; position: absolute; top: 64px; right: 0; left: 0; border-bottom: 1px solid #172031; }
  .menu-toggle { display: block; }
}
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Vidraçaria Maranhão • Vidros Temperados e Esquadrias</title>
  <meta name="description" content="Vidros temperados, box de banheiro, guarda-corpo, esquadrias de alumínio e fachadas em São José de Ribamar e região." />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="styles.css" />
  <link rel="icon" href="img/favicon.png" />
</head>
<body>
  <!-- Header -->
  <header class="header">
    <div class="container nav">
      <a href="#" class="logo">Vidraçaria<span>Maranhão</span></a>
      <nav class="menu" id="menu">
        <a href="#servicos">Serviços</a>
        <a href="#portfolio">Portfólio</a>
        <a href="#depoimentos">Depoimentos</a>
        <a href="#sobre">Sobre</a>
        <a href="#contato" class="btn btn-sm">Contato</a>
      </nav>
      <button class="menu-toggle" id="menuToggle" aria-label="Abrir menu">☰</button>
    </div>
  </header>

  <!-- Hero -->
  <section class="hero">
    <div class="container hero-grid">
      <div class="hero-text">
        <h1>Vidros temperados e esquadrias com instalação rápida e segura</h1>
        <p>Atendimento em São José de Ribamar, São Luís e região. Orçamento sem compromisso e visita técnica.</p>
        <div class="hero-actions">
          <a href="#orcamento" class="btn">Pedir orçamento</a>
          <a href="https://wa.me/5598SEUNUMERO?text=Olá,%20gostaria%20de%20um%20orçamento%20de%20vidros" class="btn btn-outline" target="_blank" rel="noopener">WhatsApp</a>
        </div>
        <ul class="selos">
          <li>🛡️ Temperado ABNT</li>
          <li>⏱️ Instalação ágil</li>
          <li>📄 Garantia e nota fiscal</li>
        </ul>
      </div>
      <div class="hero-img">
        <img src="img/hero.jpg" alt="Instalação de vidro temperado" />
      </div>
    </div>
  </section>

  <!-- Serviços -->
  <section id="servicos" class="section">
    <div class="container">
      <h2>Nossos serviços</h2>
      <p>Projetos sob medida com materiais certificados e acabamentos profissionais.</p>
      <div class="cards">
        <article class="card">
          <img src="img/box.jpg" alt="Box de banheiro" />
          <h3>Box de banheiro</h3>
          <p>Vidro temperado com roldanas inox, opções de correr ou abrir.</p>
        </article>
        <article class="card">
          <img src="img/guarda_corpo.jpg" alt="Guarda-corpo" />
          <h3>Guarda-corpo</h3>
          <p>Segurança e elegância para escadas, varandas e mezaninos.</p>
        </article>
        <article class="card">
          <img src="img/fechamento.jpg" alt="Fechamento de varanda" />
          <h3>Fechamento de varanda</h3>
          <p>Sistemas retráteis e fixos com vedação eficiente.</p>
        </article>
        <article class="card">
          <img src="img/esquadrias.jpg" alt="Esquadrias de alumínio" />
          <h3>Esquadrias de alumínio</h3>
          <p>Janelas e portas sob medida com alta durabilidade.</p>
        </article>
      </div>
    </div>
  </section>

  <!-- Portfólio -->
  <section id="portfolio" class="section alt">
    <div class="container">
      <h2>Portfólio</h2>
      <p>Alguns dos nossos projetos recentes.</p>
      <div class="grid gallery">
        <img src="img/port1.jpg" alt="Projeto 1" />
        <img src="img/port2.jpg" alt="Projeto 2" />
        <img src="img/port3.jpg" alt="Projeto 3" />
        <img src="img/port4.jpg" alt="Projeto 4" />
        <img src="img/port5.jpg" alt="Projeto 5" />
        <img src="img/port6.jpg" alt="Projeto 6" />
      </div>
    </div>
  </section>

  <!-- Depoimentos -->
  <section id="depoimentos" class="section">
    <div class="container">
      <h2>Depoimentos</h2>
      <div class="testimonials">
        <blockquote>
          <p>“Atendimento excelente e instalação impecável. Recomendo!”</p>
          <footer>— Carla M., Araçagi</footer>
        </blockquote>
        <blockquote>
          <p>“Preço justo e prazo cumprido. Ficou perfeito!”</p>
          <footer>— João P., Calhau</footer>
        </blockquote>
        <blockquote>
          <p>“Equipe organizada e cuidadosa com o acabamento.”</p>
          <footer>— Sônia R., Cohatrac</footer>
        </blockquote>
      </div>
    </div>
  </section>

  <!-- Sobre -->
  <section id="sobre" class="section alt">
    <div class="container about">
      <div>
        <h2>Sobre nós</h2>
        <p>Somos especialistas em vidro temperado e esquadrias, com equipe própria e fornecedores homologados. Atendemos residencial e comercial com foco em segurança, estética e durabilidade.</p>
        <ul class="list">
          <li><strong>Experiência:</strong> Mais de 8 anos no mercado</li>
          <li><strong>Qualidade:</strong> Vidros certificados e ferragens premium</li>
          <li><strong>Atendimento:</strong> Projeto, fabricação e instalação</li>
        </ul>
      </div>
      <div class="about-img">
        <img src="img/equipe.jpg" alt="Equipe da vidraçaria" />
      </div>
    </div>
  </section>

  <!-- Orçamento -->
  <section id="orcamento" class="section">
    <div class="container">
      <h2>Peça seu orçamento</h2>
      <p>Responda e retornamos com um orçamento detalhado.</p>
      <form id="formOrcamento" class="form">
        <div class="grid two">
          <label>
            <span>Nome</span>
            <input type="text" name="nome" required />
          </label>
          <label>
            <span>Telefone/WhatsApp</span>
            <input type="tel" name="telefone" required />
          </label>
        </div>
        <div class="grid two">
          <label>
            <span>Cidade/Bairro</span>
            <input type="text" name="cidade" required />
          </label>
          <label>
            <span>Tipo de serviço</span>
            <select name="servico" required>
              <option value="">Selecione</option>
              <option>Box de banheiro</option>
              <option>Guarda-corpo</option>
              <option>Fechamento de varanda</option>
              <option>Esquadrias de alumínio</option>
              <option>Fachada</option>
              <option>Outro</option>
            </select>
          </label>
        </div>
        <label>
          <span>Descrição do projeto</span>
          <textarea name="descricao" rows="4" placeholder="Medidas aproximadas, cor (incolor, fumê, etc.), prazos..." required></textarea>
        </label>
        <div class="grid two">
          <label>
            <span>Enviar imagens (opcional)</span>
            <input type="file" name="fotos" multiple accept="image/*" />
          </label>
          <label>
            <span>Preferência de contato</span>
            <select name="preferencia">
              <option>WhatsApp</option>
              <option>Ligação</option>
              <option>E-mail</option>
            </select>
          </label>
        </div>
        <button class="btn" type="submit">Enviar</button>
        <p class="form-status" id="formStatus" role="status" aria-live="polite"></p>
      </form>
    </div>
  </section>

  <!-- Contato -->
  <section id="contato" class="section alt">
    <div class="container contact">
      <div>
        <h2>Contato</h2>
        <ul class="contact-list">
          <li><strong>WhatsApp:</strong> <a href="https://wa.me/5598SEUNUMERO" target="_blank" rel="noopener">+55 (98) SEU NÚMERO</a></li>
          <li><strong>E-mail:</strong> contato@vidracariamaranhao.com.br</li>
          <li><strong>Endereço:</strong> São José de Ribamar, MA</li>
          <li><strong>Horário:</strong> Seg–Sáb, 8h às 18h</li>
        </ul>
        <div class="social">
          <a href="#" aria-label="Instagram">Instagram</a>
          <a href="#" aria-label="Facebook">Facebook</a>
          <a href="#" aria-label="Google Meu Negócio">Google</a>
        </div>
      </div>
      <div class="map">
        <iframe title="Mapa" src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d" loading="lazy"></iframe>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer class="footer">
    <div class="container footer-grid">
      <div>
        <a href="#" class="logo footer-logo">Vidraçaria<span>Maranhão</span></a>
        <p>© <span id="year"></span> Vidraçaria Maranhão. Todos os direitos reservados.</p>
      </div>
      <ul class="footer-links">
        <li><a href="#servicos">Serviços</a></li>
        <li><a href="#portfolio">Portfólio</a></li>
        <li><a href="#depoimentos">Depoimentos</a></li>
        <li><a href="#sobre">Sobre</a></li>
        <li><a href="#contato">Contato</a></li>
      </ul>
    </div>
    <a class="whatsapp-float" href="https://wa.me/5598SEUNUMERO?text=Olá,%20preciso%20de%20um%20orçamento" target="_blank" rel="noopener">💬</a>
  </footer>

  <script src="script.js"></script>
</body>
</html>
