# 💈 Smart Web Experience — Resenha Barbearia

> Projeto acadêmico desenvolvido para a disciplina de **Padrões Web No-Code/Low-Code** na **UniFECAF**.

---

## 📌 1. Sobre o Projeto
A **Resenha Barbearia** é um estabelecimento local de estética masculina. O objetivo deste projeto é resolver gargalos de atendimento (demora no retorno manual por WhatsApp/Instagram em horários de pico) oferecendo uma aplicação web moderna, responsiva e com agendamento/orçamento automatizado.

---

## 🚀 2. Funcionalidades Desenvolvidas
* **Calculadora Interativa de Serviços:** Cálculo em tempo real do valor acumulado e do tempo estimado do atendimento com base nos combos selecionados (Corte, Barba, Sobrancelha, Pigmentação).
* **Validação de Data e Horário:** Seleção dinâmica com sinalização visual de horários indisponíveis/ocupados para garantir o controle da agenda.
* **Encaminhamento Direto para WhatsApp:** Geração automática de mensagem formatada com todos os detalhes do orçamento e envio direto para a API do WhatsApp da barbearia.
* **Assistente Virtual com IA (Chatbot):** Atendimento 24/7 integrado para responder dúvidas frequentes sobre localização, formas de pagamento, horários e sugestões de corte.
* **Design Responsive & Mobile-First:** Interface elegante em Dark Mode otimizada para navegação rápida e fluida em smartphones.

---

## 🛠️ 3. Tecnologias & Ferramentas Utilizadas
* **Framer:** Plataforma No-Code utilizada para construção da estrutura visual, layout responsivo e hospedagem da aplicação.
* **HTML5 & CSS3:** Estruturação semântica do formulário/embed e estilização personalizada dos elementos visuais.
* **JavaScript (Vanilla JS):** Desenvolvimento da lógica da calculadora, manipuladores de eventos (`event listeners`), validação dos horários e formatação dinâmica da mensagem para o WhatsApp (`encodeURIComponent`).

---

## 💻 4. Trecho de Código Desenvolvido (JavaScript)

```javascript
// Lógica desenvolvida em JavaScript para cálculo dinâmico, validação de horários e integração com WhatsApp
document.addEventListener("DOMContentLoaded", function() {
  const checkboxes = document.querySelectorAll('.servico');
  const precoElemento = document.getElementById('preco-total');
  const tempoElemento = document.getElementById('tempo-total');
  const inputData = document.getElementById('data-agendamento');
  const selectHorario = document.getElementById('horario-agendamento');
  const btnAgendar = document.getElementById('btn-agendar');

  const numeroWhatsapp = "5511999999999"; 

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

    precoElemento.textContent = `R$ ${valorTotal.toFixed(2).replace('.', ',')}`;
    tempoElemento.textContent = `${tempoTotal} min`;

    const dataVal = inputData.value;
    const horaVal = selectHorario.value;

    if (servicosSelecionados.length > 0 && dataVal && horaVal) {
      let dataFormatada = dataVal.split('-').reverse().join('/');
      let textoMsg = `Olá! Gostaria de agendar um horário na Resenha Barbearia:\n\n*Serviços Selecionados:*\n- ${servicosSelecionados.join('\n- ')}\n\n📅 *Data:* ${dataFormatada}\n⏰ *Horário:* ${horaVal}\n💰 *Valor Total:* R$ ${valorTotal.toFixed(2).replace('.', ',')}\n⏱️ *Tempo Estimado:* ${tempoTotal} min`;
      
      btnAgendar.href = `[https://wa.me/$](https://wa.me/$){numeroWhatsapp}?text=${encodeURIComponent(textoMsg)}`;
      btnAgendar.style.opacity = "1";
      btnAgendar.style.pointerEvents = "auto";
    } else {
      btnAgendar.href = "#";
      btnAgendar.style.opacity = "0.6";
      btnAgendar.style.pointerEvents = "none";
    }
  }

  checkboxes.forEach(chk => chk.addEventListener('change', atualizarTudo));
  inputData.addEventListener('change', atualizarTudo);
  selectHorario.addEventListener('change', atualizarTudo);
});
🔗 5. Como Testar e Acessar a Solução
Link da Aplicação ao Vivo: Acessar Projeto Resenha Barbearia
