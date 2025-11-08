# Instruções para Agentes de IA

Estas instruções ajudam agentes de código a trabalhar produtivamente neste projeto.

## Visão Geral
- Projeto estático de apresentação em `index.html` usando React via UMD e Babel Standalone.
- Não há bundler, transpiler ou estrutura de pastas — tudo está em um único arquivo.
- Tailwind CSS é incluído via CDN para estilos utilitários.
- Ícones são fornecidos pela biblioteca `lucide` via CDN.

## Arquitetura
- Componente principal: `Apresentacao` definido inline em `index.html` dentro de `<script type="text/babel">`.
- Estado local: `slideAtual` controla navegação entre slides.
- Estrutura de dados: `slides` é um array de objetos com `{ icon, titulo, subtitulo, conteudo }`.
- Ícones: importados de `lucide` (`const { User, Target, ... } = lucide`).
- Renderização: `ReactDOM.createRoot(document.getElementById('root')).render(<Apresentacao />)`.

## Padrões Específicos
- Estilos: classes Tailwind diretamente nos elementos JSX.
- Navegação: botões avançar/voltar atualizam `slideAtual` com limites.
- Conteúdo: JSX rico (divs, grids, listas) para cada `conteudo` de slide.
- Não há roteamento, estado global ou requests HTTP.

## Fluxos de Trabalho do Desenvolvedor
- Desenvolvimento: editar diretamente `index.html` e recarregar o navegador.
- Testes/Build: não há testes nem build; é um site estático.
- Debug: usar Console do navegador, React DevTools, e verificação de classes Tailwind.

## Convenções
- Linguagem: Português Brasileiro.
- Organização: manter `slides` como fonte única de conteúdo; adicionar novos slides como novos objetos.
- Ícones: usar nomes da API `lucide` disponíveis via CDN.

## Integrações e Dependências
- CDNs: React 18, ReactDOM 18, Babel Standalone, Tailwind CSS, Lucide.
- `package.json` lista `lucide-react`, mas o projeto não usa bundler; dependência pode ser removida se não houver plano de usar React com bundler.

## Exemplos
- Adicionar slide:
```jsx
slides.push({
  icon: Rocket,
  titulo: "Novo Slide",
  subtitulo: "Resumo do conteúdo",
  conteudo: (<div className="p-6">Conteúdo aqui</div>)
});
```

## Publicação
- GitHub Pages: publicar como site estático; `index.html` deve estar na raiz do branch `main` ou `gh-pages`.

## Segurança
- Sem dados sensíveis; garantir que não há chaves embutidas.

## Manutenção
- Seguir DRY: evitar duplicar estruturas de layout; criar helpers inline se necessário.
- Componentizar: se crescer, mover para bundler (Vite) e dividir componentes.