# Garcia Apps

Community App Store pessoal para umbrelOS.


# PROMPT IA
```
Tenho um servidor umbrelOS (x86_64 / amd64) e mantenho uma Community App Store
própria no GitHub para instalar apps que não estão na loja oficial.

CONTEXTO DA MINHA LOJA
- Repo público: https://github.com/avcgarcia/umbrel-apps
- umbrel-app-store.yml na raiz: id "avcgarcia", name "Garcia Apps"
- Cada app fica numa pasta "avcgarcia-<nome>/" com umbrel-app.yml e docker-compose.yml
- Apps já na loja: avcgarcia-artschool (porta 8742)
- Apps instalados no Umbrel: adguard-home, immich, myspeed, openclaw, opencode,
  tailscale, avcgarcia-artschool
- Tenho um GitHub Action (.github/workflows/update-apps.yml) que roda diariamente,
  consulta o Docker Hub e atualiza sozinho a tag, o digest e o "version" de cada
  app quando sai versão nova. Ele só funciona com tags semver (ex: 1.2.3), nunca "latest".

PADRÕES QUE QUERO SEGUIR (aprendidos na instalação anterior)
1. Antes de tudo, verifique no Docker Hub se a imagem tem build linux/amd64
   e quais tags semver existem.
2. Fixe a imagem como "imagem:X.Y.Z@sha256:<digest>" e use o mesmo X.Y.Z no "version".
3. Inclua a linha "icon:" no umbrel-app.yml DESDE O INÍCIO, apontando para
   https://raw.githubusercontent.com/avcgarcia/umbrel-apps/main/avcgarcia-<nome>/icon.svg
   (ou .png), e me entregue o arquivo do ícone (procure o logo oficial do projeto).
   O Umbrel copia o manifest na instalação, então adicionar ícone depois exige
   editar via SSH em /home/umbrel/umbrel/app-data/<id>/umbrel-app.yml e reiniciar.
4. No docker-compose.yml use o serviço app_proxy com
   APP_HOST: avcgarcia-<nome>_<servico>_1 e APP_PORT = porta interna do container.
5. Porta do umbrel-app.yml deve ser única (não usar 8742).
6. Dados persistentes em ${APP_DATA_DIR}/data; se o app precisar ler arquivos
   do meu Files, use ${UMBREL_ROOT}/home/<Pasta> (Downloads, Documents, Photos, Videos).
7. Se o app tiver vários containers (banco, redis etc.), inclua todos no compose.

COMO QUERO SER INSTRUÍDO
- Gere os arquivos prontos e valide o YAML antes de me entregar (de preferência
  num .zip só com a pasta avcgarcia-<nome>/).
- Me explique passo a passo, com calma, onde clicar no GitHub (upload dentro do
  repo, pela interface web) e no Umbrel (App Store → ⋯ → Community App Stores →
  Garcia Apps → Instalar).
- Diga se preciso criar alguma pasta no Files antes de instalar.
- Responda em português.

APP QUE QUERO INSTALAR AGORA:
<cole aqui o link do GitHub ou Docker Hub do app>
```
