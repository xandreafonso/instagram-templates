# Templates disponíveis

- Capa `cover.html`
- Conteúdo `content.html`
- Chamada para ação `cta.html`

Os templates foram construídos com HTML e TailwindCSS. Cada um possui "espaços" a serem preenchidos. Cada "espaço" a ser preenchido corresponde a uma propriedade de contexto usada pelo template.

Comandos usados para aplicar o template:

- `template_engine` é usado para aplicar o template em si
- `playwright_flow` é usado para gerar a imagem com base no arquivo HTML criado pela engine

Ex:

```bash
template_engine --template "$WORKSPACE/instagram-templates/cover.html" --context '{"headline": "..."}' --output "$WORKSPACE/.temp/instagram-posts-carrossel/CN00000000A/slide-01--cover.html"
playwright_flow --theme dark --page-goto "$WORKSPACE/.temp/instagram-posts-carrossel/CN00000000A/slide-01--cover.html" --screenshot '.slide' --ss-path "$WORKSPACE/.temp/instagram-posts-carrossel/CN00000000A/slide-01--cover.png"
```

Nota: repare que "CN00000000A" se refere ao código do conteúdo/carrossel que estiver sendo criado.
Nota: no caso de aplicar o template nos slides de conteúdo, cada arquivo de saída deve conter um número no nome referente a posição do slide no carrossel como um todo.

Caso seja preciso, pode-se enviar os slides para o storage do S3 com o comando `s3`. Abaixo temos um exemplo do envio de todos os arquivos de uma pasta. A ideia do exemplo foi que os slides foram salvos em uma pasta e usamos o path da mesma como parâmetro para o script `s3`.

```bash
s3 --profile scripts --upload "$WORKSPACE/.temp/instagram-posts-carrossel/CN00000000A/" --prefix public/instagram-posts/xandreafonso/CN00000000A
```

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