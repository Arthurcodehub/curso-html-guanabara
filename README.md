# 🥽 Google Glass — Site Responsivo

Projeto de estudo do curso de **HTML5 e CSS3** ([Curso em Vídeo](https://www.cursoemvideo.com/) - Gustavo Guanabara), com camada de **responsividade** adicionada para funcionar bem em desktop, tablet e celular.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)

## 🔗 Demo

🔗 https://arthurcodehub.github.io/curso-html-guanabara/

## 🚀 Tecnologias

- **HTML5** — marcação semântica (`header`, `nav`, `section`, `article`, `aside`, `footer`)
- **CSS3** — Flexbox, Media Queries, `box-sizing`, transições e efeitos de hover
- **JavaScript** — troca dinâmica do ícone do menu

## 📄 Páginas

| Página | Descrição |
|---|---|
| `index.html` | Home com a matéria principal sobre o Google Glass |
| `specs.html` | Especificações técnicas com imagem de mapa clicável |
| `fotos.html` | Galeria de fotos com efeito de zoom no hover |
| `multimidia.html` | Player de áudio e vídeo |
| `fale-conosco.html` | Formulário de contato com diversos inputs HTML5 |

## 📱 Responsividade

Layout adaptado em dois breakpoints principais:

- **≤ 900px** (tablet) — cabeçalho e menu deixam de usar posicionamento absoluto, conteúdo principal e lateral empilham
- **≤ 600px** (celular) — menu em lista vertical, tipografia e tabelas ajustadas para telas pequenas

Toda a responsividade está isolada em `_css/responsivo.css`, carregado por último, sem alterar os arquivos CSS originais do curso.

## ▶️ Como rodar localmente

```bash
git clone https://github.com/Arthurcodehub/curso-html-guanabara.git
cd curso-html-guanabara
```

Depois é só abrir o `index.html` no navegador, ou rodar um servidor local:

```bash
npx serve .
# ou
python3 -m http.server 8000
```

## 🤝 Como contribuir

Achou um erro, um bug visual em alguma tela, ou tem uma sugestão de melhoria? Fique à vontade para contribuir:

1. Abra uma **[Issue](../../issues)** descrevendo o problema (se possível, com print e o tamanho de tela/navegador usado)
2. Ou, se já tiver a correção, **faça um fork**, crie uma branch (`git checkout -b fix/nome-do-ajuste`), commit suas mudanças e abra um **Pull Request** explicando o que foi alterado
3. PRs pequenos e focados em uma única mudança são mais fáceis de revisar e aceitar

Toda contribuição é bem-vinda — desde correção de digitação até melhorias de acessibilidade e responsividade. 🙌

## 👤 Créditos

- Projeto base: Gustavo Guanabara — [Curso em Vídeo](https://www.cursoemvideo.com/)
- Responsividade e ajustes: **Arthur** **Fernandes**

## 📝 Licença

Projeto com fins educacionais, desenvolvido durante o curso de HTML5/CSS3.
