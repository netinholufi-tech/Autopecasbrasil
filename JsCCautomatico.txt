// Rolagem suave ao clicar nos links do menu
document.querySelectorAll("nav a").forEach(link => {
  link.addEventListener("click", function(e) {
    e.preventDefault();
    const sectionId = this.textContent.toLowerCase();
    const section = document.querySelector("." + sectionId);
    if (section) {
      section.scrollIntoView({ behavior: "smooth" });
    }
  });
});

// Animação nos cards
const cards = document.querySelectorAll(".card");
cards.forEach(card => {
  card.addEventListener("mouseenter", () => {
    card.style.transform = "scale(1.05)";
    card.style.transition = "transform 0.3s";
  });
  card.addEventListener("mouseleave", () => {
    card.style.transform = "scale(1)";
  });
});

// Validação simples do formulário de e-mail
const button = document.querySelector("footer button");
button.addEventListener("click", () => {
  const emailInput = document.querySelector("footer input[type='email']");
  const email = emailInput.value.trim();

  if (email === "" || !email.includes("@")) {
    alert("Por favor, insira um e-mail válido.");
  } else {
    alert("Obrigado por se cadastrar! Você receberá nossas ofertas em breve.");
    emailInput.value = "";
  }
});

// Carrossel automático para Serviços e Depoimentos
function iniciarCarrossel(seletor, intervalo = 3000) {
  const container = document.querySelector(seletor);
  if (!container) return;

  let scrollPos = 0;
  setInterval(() => {
    scrollPos += 250; // largura aproximada de cada card
    if (scrollPos >= container.scrollWidth) {
      scrollPos = 0; // reinicia o carrossel
    }
    container.scrollTo({
      left: scrollPos,
      behavior: "smooth"
    });
  }, intervalo);
}

// Ativar carrosséis
iniciarCarrossel(".servicos .cards", 4000);
iniciarCarrossel(".depoimentos .cards", 5000);
