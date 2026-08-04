## Templates disponíveis

- Capa `cover.html`
- Conteúdo `content.html`
- Chamada para ação `cta.html`

### Capa

O `cover.html` precisa de um contexto com a propriedade `headline`.

```bash
template_engine --template cover.html --context '{"headline": "Headline do post"}' --output /path/cover.html
```

Exemplo de contexto para `cover.html`:

```json
{
  "headline": "<span class=\"text-4xl leading-normal text-center\">Será que faz sentido ter um <b>sistema operacional</b> de IA?</span>",
}
```

É interessante encapsular a headline com uma tag `span` e as classes CSS `text-4xl leading-normal text-center`. Para deixar uma palavra ou termo em negrito, use a tag `b`.

### Conteúdo

O `content.html` precisa da propriedade `content`.

```bash
template_engine --template content.html --context '{"content": "Conteúdo do post"}' --output /path/content.html
```

Exemplo de contexto para `content.html`:

```json
{
  "content": "<div class=\"text-2xl flex flex-col gap-6\"><p>Tem gente vendendo SO de inteligência artificial com o discurso de que você vai automatizar tudo dentro da sua empresa.</p><p>Só pra constar: não, isso de automatizar tudo não vai acontecer. Digo mais: se o seu processo apenas não piorar, você tá no lucro.</p></div>"
}
```

Via de regra o conteúdo será representado por um texto. Sendo assim, é interessante encapsular o conteúdo com uma tag `div` e as classes CSS `text-2xl flex flex-col gap-6`. Para melhor formatação, cada parágrafo deve estar dentro da tag `p`.

### Chamada para ação

O `cta.html` precisa da propriedade `cta`.

```bash
template_engine --template cta.html --context '{"cta": "Chamada para ação"}' --output /path/cta.html
```

Exemplo de contexto para `cta.html`:

```json
{
  "cta": "<span class=\"text-4xl leading-normal text-center text-sky-600\">Se você quer aplicar IA de maneira realmente inteligente, <b class=\"underline text-zinc-950 dark:text-white\">toca no link da bio</b>.</span>"
}
```

É interessante encapsular o CTA em uma tag `span` e as classes CSS `text-4xl leading-normal text-center text-sky-600`. Para deixar uma palavra ou termo em negrito, use a tag `b`. 

Como o CTA tem uma cor específica (o sky), caso seja necessário destacar um trecho, é preciso usar a tag `b` com classes CSS do tailwind `text-zinc-950` e `dark:text-white`. Isso faz com que o tema escuro e claro sejam compatíveis.


## Usar os templates

Use o comando `template_engine` para aplicar um template.

```bash
template_engine --template cover.html --context '{}' --output /path/cover.html
```

## Gerar Imagem

Uma vez que o arquivo html tiver sido gerado a partir do template, então pode-se gerar a imagem do slide do carrossel.

```bash
playwright_flow --page-goto '/caminho/completo/cover.html' --screenshot '.slide' --ss-path /path/cover.png
```
