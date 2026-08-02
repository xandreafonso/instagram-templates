# Assets

Nos templates, nós usamos assets publicos para não depender do caminho relativo para a pasta assets.

Os assets já estão no s3. Se por algum motivo eles tiverem sido apagadas, pode carregá-los novamente com o comando `s3`.

```bash
s3 --profile scripts --prefix public/temp --upload assets/alexandre.png
```

# Usando templates

Use o comando templates para interpolar com a copy do post.

```bash
template --template cover.html --context data-sample.json --output .temp/cover.html
```