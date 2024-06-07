---
layout: page
title: Envíame un correo
description: >
  Puedes enviarme un correo a través de esta página.
sitemap: false
---


%%<form>
%%  <div class="form-group">
%%    <label for="emailInput">Tu correo electrónico</label>
%%    <input type="email" class="form-control" id="emailInput" placeholder="nombre@example.com">
%%  </div>
%%  <div class="form-group">
%%    <label for="subjectInput">Asunto</label>
%%    <input type="subject" class="form-control" id="subjectInput" placeholder="Oferta de sponsor">
%%  </div>
%%  <div class="form-group">
%%    <label for="contentInput">Example textarea</label>
%%    <textarea class="form-control" id="contentInput" rows="3"></textarea>
%%  </div>
%%  <div class="form-group">
%%    <button type="submit" class="btn btn-primary">Enviar</button>
%%  </div>
%%</form>



<form id="contactForm">
  <div class="form-group">
    <label for="emailInput">Tu correo electrónico</label>
    <input type="email" class="form-control" id="emailInput" placeholder="nombre@example.com" required>
  </div>
  <div class="form-group">
    <label for="subjectInput">Asunto</label>
    <input type="text" class="form-control" id="subjectInput" placeholder="Oferta de sponsor" required>
  </div>
  <div class="form-group">
    <label for="contentInput">Mensaje</label>
    <textarea class="form-control" id="contentInput" rows="3" required></textarea>
  </div>
  <div class="form-group">
    <button type="submit" class="btn btn-primary">Enviar</button>
  </div>
</form>

<script>
document.getElementById('contactForm').addEventListener('submit', function(event) {
  event.preventDefault();

  const email = document.getElementById('emailInput').value;
  const subject = document.getElementById('subjectInput').value;
  const content = document.getElementById('contentInput').value;

  const issueTitle = `Email from ${email}: ${subject}`;
  const issueBody = `**De:** ${email}\n\n**Asunto:** ${subject}\n\n**Mensaje:**\n${content}`;

  fetch('https://api.github.com/repos/NeddM/NeddM.github.io/issues', {
    method: 'POST',
    headers: {
      %%'Authorization': 'token TU_GITHUB_PERSONAL_ACCESS_TOKEN',
      'Accept': 'application/vnd.github.v3+json',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      title: issueTitle,
      body: issueBody
    })
  })
  .then(response => {
    if (response.ok) {
      alert('Issue creada exitosamente');
    } else {
      return response.json().then(error => { throw new Error(error.message) });
    }
  })
  .catch(error => {
    console.error('Error:', error);
    alert('Hubo un error al crear la issue');
  });
});
</script>
