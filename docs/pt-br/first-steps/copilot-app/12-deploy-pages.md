---
title: "Lição 12 - Implante o site com o GitHub Pages"
description: "Use o aplicativo GitHub Copilot para configurar um workflow do Pages, revisar a pull request e verificar o Space Quiz publicado."
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

Publique o Space Quiz com o GitHub Pages para que todos possam acessá-lo. O Copilot pode preparar o workflow e orientar a implantação, mas você é responsável por revisar as alterações e confirmar que o site está disponível.

Nesta lição, você vai:

- pedir ao Copilot que configure a implantação no GitHub Pages.
- revisar o workflow e a pull request antes do merge.
- acompanhar a implantação e verificar o site publicado.

## Cenário

O Space Quiz já está em um repositório do GitHub, mas as pessoas ainda precisam de uma forma simples de experimentá-lo. Publicar o site de arquivo único com o GitHub Pages permite acessá-lo por uma URL pública sem adicionar um servidor ou dependências de runtime.

## Peça ao Copilot para preparar a implantação

> [!WARNING]
> Criar uma pull request pode confirmar e enviar código. Revise as configurações de aprovação e o repositório de destino antes de enviar este prompt. Com **Approve all**, não espere outra solicitação de confirmação.

Na sessão do aplicativo Copilot para `space-quiz`, envie este prompt:

```plaintext
Prepare a GitHub Pages deployment for this repository. Create a GitHub Actions workflow that builds the website if needed and deploys it to GitHub Pages after changes reach the default branch. Add a README describing the app and how to run it locally if one does not already exist. Create a pull request with these changes and report its link and any required Pages settings or permissions. Do not merge, enable auto-merge, change Pages settings, or deploy. Stop and wait for my review.
```

## Revise o workflow e a pull request

1. Confirme se o README só foi adicionado caso ainda não existisse no repositório.
2. Revise as alterações da pull request, incluindo as etapas de build e implantação do workflow, os gatilhos e as permissões.
3. Confirme que o workflow implanta a partir da branch padrão, e não de uma pull request ainda não mesclada.
4. Peça as correções necessárias e revise o diff atualizado. Aguarde a aprovação nas verificações obrigatórias da pull request antes de autorizar o merge.

## Autorize o merge e a implantação

> [!WARNING]
> O prompt a seguir autoriza o agente a mesclar a pull request revisada, alterar as configurações do Pages do repositório e publicar o site. Envie-o somente depois de concluir a revisão e confirmar o repositório e a pull request. Dependendo das configurações de aprovação, essas ações podem ocorrer sem outra solicitação de confirmação.

Substitua `<PR_NUMBER>` pelo número da pull request revisada e envie este prompt separadamente:

```plaintext
I have reviewed pull request <PR_NUMBER> in this repository and authorize its merge and deployment. Enable GitHub Pages using GitHub Actions, merge that pull request only after required checks pass, and monitor the deployment until it succeeds. Report the final URL of the live website. If you lack permission to enable Pages or merge, tell me exactly what I need to approve or do; do not report success until the site is live.
```

![Diagrama de três etapas: uma pull request do space-quiz mesclada; uma execução bem-sucedida de Deploy website no GitHub Actions com as etapas Build website, Upload artifact e Deploy to Pages; e o Space Quiz publicado em yourname.github.io/space-quiz/.](../../../_images/first-steps-app-pages-deploy.svg)

## Verifique a implantação

1. Acompanhe a execução de implantação do GitHub Actions até a conclusão bem-sucedida.
2. Abra a URL informada e confirme que o Space Quiz carrega.

Se o agente não puder habilitar o Pages nem mesclar a pull request, siga as instruções específicas fornecidas. Não considere a tarefa concluída até que a implantação seja bem-sucedida e o site esteja disponível.

## Resumo e próximos passos

O Space Quiz está disponível como um site publicado, e você verificou a implantação em vez de confiar apenas no relato do agente. Continue para a [Lição 13: Revisão e próximos passos][next-lesson].

[next-lesson]: ../13-review/
