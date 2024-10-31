# Visão Geral 🚀💡😎👽

Este repositório contém o código do site de portfólio pessoal de Anderson Gaitolini, hospedado em [https://anderson.gaitolini.com.br/](https://anderson.gaitolini.com.br/). O objetivo do site é apresentar projetos, habilidades e experiências de Anderson como desenvolvedor, bem como integração com um contador de visitas que é alimentado pelo backend desenvolvido em Go.

Repositório do frontend: [Gaitolini-WebPage](https://github.com/gaitolini/Gaitolini-WebPage)

## Tecnologias Utilizadas
- **HTML/CSS e JavaScript**: Usado para a estruturação, estilização e interatividade da página.
- **JQuery**: Biblioteca JavaScript utilizada para manipulação do DOM e facilitar as requisições AJAX.
- **Cloudflare Tunnel**: Utilizado para garantir o acesso seguro entre o frontend e o backend.
- **Integração com Backend**: O site faz chamadas para a API do backend hospedado no Fly.io para obter o número de visitas ao site.

## Funcionalidades
- **Contador de Visitas**: A home do site exibe uma contagem de quantas visitas únicas o site recebeu. Isso é feito através de uma integração com a API REST desenvolvida em Go, garantindo uma visão precisa do número de visitantes.
- **Portfólio de Projetos**: Apresentação de diferentes projetos realizados, incluindo o uso de Delphi, integração com APIs, IoT, e projetos em nuvem.

## Integração com Backend e Fly.io
O site faz uso do backend hospedado no Fly.io para exibir a contagem de visitas. Para evitar problemas de CORS, o Cloudflare Tunnel é utilizado para prover um canal seguro entre o frontend e o backend, garantindo que todas as requisições sejam feitas de forma segura e sem erros.

## Como Conectar o Frontend ao Backend
1. No backend, certifique-se de que a API esteja acessível publicamente no Fly.io. O endpoint usado pelo frontend é algo como: `https://counterwebsitexyz.fly.dev/api/contador-visitas`.
2. O frontend faz uma requisição AJAX usando JavaScript para exibir o número de visitas na página inicial.
3. Use o `sessionStorage` no JavaScript do frontend para garantir que a contagem de visitas não seja incrementada repetidamente se o usuário navegar entre as páginas.

### Exemplo de Requisição AJAX no Frontend
```javascript
function atualizarContador() {
  fetch("https://counterwebsitexyz.fly.dev/api/contador-visitas")
    .then(response => {
      if (!response.ok) {
        throw new Error("Erro ao carregar contador de visitas.");
      }
      return response.json();
    })
    .then(data => {
      const visitas = data.visitas;
      const textoVisitas = `Você é o meu ${visitas}º visitante, que satisfação ver você aqui!`;
      document.getElementById("visitor-counter").innerText = textoVisitas;
    })
    .catch(error => {
      console.error("Erro ao buscar o contador de visitas:", error);
    });
}
```

## Habilidades Demonstradas
- **Frontend Development**: Desenvolvimento de página responsiva com HTML, CSS e JavaScript.
- **Integração com APIs**: Consumo de uma API REST para funcionalidade do contador de visitas.
- **Cloudflare Tunnel**: Configuração e uso para conexões seguras entre frontend e backend.
- **Infraestrutura e Cloud**: Deploy do backend e integração usando Fly.io.

## Referências ao Backend
Para ver o backend que fornece o contador de visitas para este site, visite o repositório: [Count-Web-Site](https://github.com/gaitolini/Count-Web-Site).
