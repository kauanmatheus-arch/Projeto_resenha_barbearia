# 💈 Smart Web Experience — Resenha Barbearia

> Projeto acadêmico desenvolvido para a disciplina de **Padrões Web No-Code/Low-Code** na **UniFECAF**.

---

## 📌 1. Sobre o Projeto
A **Resenha Barbearia** é um estabelecimento local de estética masculina. O objetivo deste projeto é resolver gargalos de atendimento (demora no retorno manual por WhatsApp/Instagram em horários de pico) oferecendo uma aplicação web moderna, responsiva e com agendamento/orçamento automatizado.

---

## 🚀 2. Funcionalidades Desenvolvidas
* **Calculadora Interativa de Serviços:** Cálculo em tempo real do valor acumulado e do tempo estimado do atendimento com base nos combos selecionados (Corte, Barba, Sobrancelha, Pigmentação).
* **Validação de Data e Horário:** Seleção dinâmica com sinalização visual de horários indisponíveis/ocupados.
* **Encaminhamento Direto para WhatsApp:** Geração automática da mensagem formatada com os detalhes do orçamento e envio direto para a API do WhatsApp da barbearia.
* **Assistente Virtual com IA (Chatbot):** Atendimento 24/7 integrado para sanar dúvidas frequentes sobre localização, formas de pagamento e estilos de corte.
* **Design Responsive & Mobile-First:** Interface elegante em Dark Mode otimizada para navegação rápida em smartphones.

---

## 🛠️ 3. Tecnologias & Ferramentas Utilizadas
* **Framer:** Plataforma No-Code utilizada para construção da estrutura visual, layout responsivo e hospedagem da aplicação.
* **HTML5 & CSS3:** Estruturação semântica do formulário/embed e estilização personalizada dos elementos visuais.
* **JavaScript (Vanilla JS):** Desenvolvimento do motor da calculadora, escutadores de eventos (`event listeners`), validação de seleção de horários e formatação dinâmica da URL do WhatsApp (`encodeURIComponent`).

---

## 💻 4. Trecho de Código Desenvolvido (JavaScript)
```javascript
// Exemplo da lógica desenvolvida para cálculo dinâmico e integração com WhatsApp
function atualizarTudo() {
  let valorTotal = 0;
  let tempoTotal = 0;
  let servicosSelecionados = [];

  checkboxes.forEach(chk => {
    if (chk.checked) {
      valorTotal += parseFloat(chk.value);
      tempoTotal += parseInt(chk.getAttribute('data-tempo'));
      servicosSelecionados.push(chk.getAttribute('data-nome'));
    }
  });

  if (servicosSelecionados.length > 0 && inputData.value && selectHorario.value) {
    let textoMsg = `Olá! Gostaria de agendar na Resenha Barbearia:\n\n*Serviços:* ${servicosSelecionados.join(', ')}\n📅 *Data:* ${inputData.value}\n⏰ *Horário:* ${selectHorario.value}\n💰 *Total:* R$ ${valorTotal.toFixed(2)}`;
    btnAgendar.href = `[https://wa.me/5511999999999?text=$](https://wa.me/5511999999999?text=$){encodeURIComponent(textoMsg)}`;
  }
}

---

## 🔗 5. Como Testar e Acessar a Solução
* **Link da Aplicação ao Vivo:** [Acessar Projeto Resenha Barbearia](https://simplified-basis-644170.framer.app)

