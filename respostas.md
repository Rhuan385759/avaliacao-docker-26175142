# Respostas · Avaliação Prática de Docker · ViaSerra Transportes (Turma B)

Nome: Rhuan Mendes dos Santos
Matrícula: 26175142
Usuário do GitHub: Rhuan385759
Usuário do Docker Hub: rhuan0000

Responda com as suas palavras e com o que aconteceu na SUA máquina. Resposta curta e certa vale mais
do que texto longo copiado. Resposta que contradiz o seu próprio Dockerfile vale zero.

## Parte 1 · Dockerfile do portal

1. Qual imagem base você usou e qual o tamanho final da imagem do portal (saída de `docker images`)?
Resposta: Usei a imagem base `nginx:alpine`. O tamanho final da imagem é `73.6 MB`.


2\. Em qual pasta do container o Nginx procura os arquivos do site? Mostre o comando que você usou para conferir que o `index.html` está lá dentro.

&#x20;  Resposta: Pasta: `/usr/share/nginx/html`

&#x20;            Comando: `docker exec -it portal ls -l /usr/share/nginx/html`



## Parte 2 · Docker Hub

3\. Nome completo da imagem publicada e link público do repositório no Docker Hub.
   Resposta: - Nome completo: `rhuan0000/viaserra-portal:1.0-26175142`

&#x20;            - Link público: `https://hub.docker.com/r/rhuan0000/viaserra-portal`



4\. Se você mudar o HTML, quais comandos precisa rodar para que a versão nova chegue ao Docker Hub?

&#x20;  Resposta: `docker build -t rhuan0000/viaserra-portal:1.0-26175142 ./portal`

&#x20;            `docker push rhuan0000/viaserra-portal:1.0-26175142`



## Parte 3 · Página de manutenção

5. Preencha uma linha por defeito encontrado. Defeito inexistente listado aqui desconta pontos.

|#|Instrução|O que estava errado|O que você viu acontecer|Como corrigiu|
|-|-|-|-|-|
|1     |FROM|A tag da imagem base do Nginx estava no Dockerfile|Ocorreu erro no build da imagem ( not found)|Corrigido para FROM nginx:alpine no Dockerfile|
|2|COPY|O caminho dos arquivos do site de manutenção estava incorreto no Dockerfile|O container subia, mas exibia a tela padrão do Nginx (Welcome to nginx!)|Corrigido para COPY html/ /usr/share/nginx/html/|
|3|EXPOSE|A porta exposta do container estava configurada incorretamente|A página de manutenção não ficava acessível na porta do host no navegador|Ajustado a porta no container/Compose para 7042:80|

6. Qual a diferença entre `-p 7042:80` e `-p 80:7042` no `docker run`? Qual dos dois números é a porta do container?

&#x20;    Resposta: - `-p 7042:80` mapeia a porta 7042 do host para a porta 80 do container.

&#x20;              - `-p 80:7042` mapeia a porta 80 do host para a porta 7042 do container.

&#x20;              O segundo número (`80`) é a porta do container.



## Parte 4 · Primeiro docker-compos

7\. Escreva os dois comandos `docker run` que fariam o mesmo que o seu `docker-compose.yml`.
   Resposta: `docker run -d --name portal -p 8042:80 rhuan0000/viaserra-portal:1.0-26175142`

&#x20;            `docker run -d --name manutencao -p 7042:80 viaserra-manutencao`


8\. Qual comando derruba os dois containers de uma vez?

&#x20;  Resposta: `docker compose down`



## Verificador

9. Código de conclusão impresso pelo verificador:

```
Resposta: VIASERRA-26175142-F7132EA3


```

