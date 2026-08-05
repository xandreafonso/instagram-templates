# Templates disponíveis

- Capa `cover.html`
- Conteúdo `content.html`
- Chamada para ação `cta.html`

Cada template possui "espaços" a serem preenchidos. Cada "espaço" a ser preenchido corresponde a uma propriedade de contexto usada pelo template.

Comandos usados para aplicar o template:

- `template_engine` é usado para aplicar o template em si
- `playwright_flow` é usado para gerar a imagem com base no arquivo HTML gerado pela engine

Ex:

```bash
template_engine --template /workspace/instagram-templates/cover.html --context '{"headline": "..."}' --output /workspace/.temp/CN00000000A/cover.html
playwright_flow --page-goto /workspace/.temp/CN00000000A/cover.html --screenshot '.slide' --ss-path /workspace/.temp/CN00000000A/cover.png
```

Nota: no caso de aplicar o template nos slides de conteúdo, cada arquivo de saída deve conter um número no nome referente a posição do slide no carrossel como um todo.

## Capa

O `cover.html` precisa de um contexto com a propriedade `headline`.

Exemplo de contexto para `cover.html`:

```json
{
  "headline": "<span class=\"text-4xl leading-normal text-center\">Será que faz sentido ter um <b>sistema operacional</b> de IA?</span>",
}
```

É interessante encapsular a headline com uma tag `span` e as classes CSS `text-4xl leading-normal text-center`. Para deixar uma palavra ou termo em negrito, use a tag `b`.

## Conteúdo

O `content.html` precisa da propriedade `content`.

Exemplo de contexto para `content.html`:

```json
{
  "content": "<div class=\"text-2xl flex flex-col gap-6\"><p>Tem gente vendendo SO de inteligência artificial com o discurso de que você vai automatizar tudo dentro da sua empresa.</p><p>Só pra constar: não, isso de automatizar tudo não vai acontecer. Digo mais: se o seu processo apenas não piorar, você tá no lucro.</p></div>"
}
```

Via de regra o conteúdo será representado por um texto. Sendo assim, é interessante encapsular o conteúdo com uma tag `div` e as classes CSS `text-2xl flex flex-col gap-6`. Para melhor formatação, cada parágrafo deve estar dentro da tag `p`.

## Chamada para ação

O `cta.html` precisa da propriedade `cta`.

Exemplo de contexto para `cta.html`:

```json
{
  "cta": "<span class=\"text-4xl leading-normal text-center text-sky-600\">Se você quer aplicar IA de maneira realmente inteligente, <b class=\"underline text-zinc-950 dark:text-white\">toca no link da bio</b>.</span>"
}
```

É interessante encapsular o CTA em uma tag `span` e as classes CSS `text-4xl leading-normal text-center text-sky-600`. Para deixar uma palavra ou termo em negrito, use a tag `b`. 

Como o CTA tem uma cor específica (o sky), caso seja necessário destacar um trecho, é preciso usar a tag `b` com classes CSS do tailwind `text-zinc-950` e `dark:text-white`. Isso faz com que o tema escuro e claro sejam compatíveis.