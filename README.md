[![Build and Deploy to Cloud Run](https://github.com/Giunossauro/treino-google-cloud-platform/actions/workflows/google-cloudrun-source.yml/badge.svg)](https://github.com/Giunossauro/treino-google-cloud-platform/actions/workflows/google-cloudrun-source.yml)

Este respositório esta sendo criado para estudar maneiras de integrar um repositório ao Google Cloud Platform com Continuous Deployment, para registrar/atualizar um container no Container Registry com a imagem Docker gerada a partir do repositório e fazer o deploy do container gerado/atualizado no Cloud Run.

Tentarei primeiro com trigger de serviço do Cloud Platform, depois tentarei usando o GitHub Actions.

Na verdade, eu tenho outro repositório onde já pratiquei um pouco, o "treino-git-flow-e-gh-actions", que está tendo o resultado final que espero deste (Continuous Deployment), mas estou tendo erros cuja fonte exata não consigo identificar (e não é erro de porta, como diz a mensagem de erro no Workflow do GitHub Actions) ao tentar replicar a mesma infra com o mesmo código fonte.

### Tentativa com o trigger:

O app gerado com o comando:

```express --view=pug treino-google-cloud-platform```

funciona conforme esperado com as configurações padrões ao criar no cloud run um novo serviço padrão com trigger de push padrão na branch main

Opções que precisaram ser alteradas fora do padrão do serviço:
- Continuously deploy new revisions from a source repository
- SET UP WITH CLOUD BUILD
- Select repository (require connect to GitHub)
- Build Type Option: Go, Node.js, Python, Java, .NET Core, Ruby or PHP via Google Cloud's buildpacks 
- Authentication: Allow unauthenticated invocations

Todas as outras opções não tiveram alterações, mantendo valores padrões.

### Tentativa com GitHub Actions

Seguindo o tutorial do artigo [CI/CD — GitHub actions and Google Cloud Build triggers](https://medium.com/devops-techable/github-actions-and-google-cloud-build-triggers-d55aceb96e68), no Medium, criei um trigger no GitHub Actions para ativar o trigger no Cloud Run... Funciona bem e gera o badge para mim!
