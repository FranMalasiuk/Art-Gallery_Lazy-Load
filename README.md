# 🎨 Art Gallery - Lazy Load

Este é um projeto simples de galeria de arte que utiliza **Lazy Loading** com `IntersectionObserver` para otimizar o carregamento das imagens.

## ✨ Objetivo

Carregar imagens de alta resolução **apenas quando elas estiverem visíveis na tela**, melhorando a performance da página.

## 🛠 Tecnologias

- HTML5
- CSS3
- JavaScript (IntersectionObserver)

## 🚀 Como funciona

As imagens da galeria inicialmente são carregadas em baixa resolução (usando `w=10` na URL).  
Quando o usuário faz scroll e a imagem entra na área visível da tela, o `IntersectionObserver` troca dinamicamente a URL para uma versão de maior resolução (`w=1000`).

Exemplo de trecho do código JavaScript:
```js
const images = document.querySelectorAll(".image-container img");

const observer = new IntersectionObserver((entries, observer) => {
    entries.forEach(entry => {
        if (!entry.isIntersecting) return;

        const image = entry.target;
        image.src = image.src.replace("w=10", "w=1000");
    });
}, {});

images.forEach((image) => {
    observer.observe(image);
});
