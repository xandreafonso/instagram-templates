# Assets

Nos templates, nós usamos assets publicos para não depender do caminho relativo para a pasta assets.

Os assets já estão no s3. Se por algum motivo eles tiverem sido apagadas, pode carregá-los novamente com o comando `s3`.

```bash
s3 --profile scripts --prefix public/temp --upload assets/alexandre.png
```

# Usando templates

Use o comando `template_engine` para interpolar com a copy do post.

```bash
template_engine --template cover.html --context data-sample.json --output .temp/cover.html
```

# Gerando Imagem

Use o comando `playwright_flow` para gerar a imagem.

```bash
playwright_flow --page-goto 'C:\Users\afons\Documents\Workspace\instagram-templates\.temp\cover.html' --screenshot '.slide' --ss-path .temp/cover.png
```
