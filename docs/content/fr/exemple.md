---
title: Exemple d’Action
description: Un petit exemple d'Action
position: 2
category: Introduction
---

<tuto-video :link="'https://www.youtube-nocookie.com/embed/6y-Y1aL4DfY'" :title="'Exemple d’Action - Tuto GitHub Actions'"></tuto-video>

## Déclaration

Chaque GitHub Action doit être composée au minimum d’un nom, d’une liste d'événement(s) et d’une liste d’action(s), déclarés dans leur balise réspective : `name`, `on` et `jobs`.

```yaml
# file: linting.py.yml
name: Linting
on: [push]
jobs:
  styles: # job key
    runs-on: ubuntu-18.04
    steps:
      - uses: actions/checkout@master
      - uses: actions/setup-python@v1
      - uses: whynothugo/python-linting@master
```

## Les jobs

Les jobs sont composés d’une clé (nom unique), d’un environnement (balise `runs-on`) et d’une liste d’étapes à réaliser (balise `steps`).

Dans cet exemple, le job `styles` utilise un environnement linux (`ubuntu`) et est composé de 3 étapes.

Chaque étape n’est en réalité qu’un appel à une autre GitHub Actions, identifiable sous cette forme : `<nom du créateur⋅rice>`/`<répo d’origine>`@`<version ou branche>`. Les Actions avec comme créateur `actions` sont mis à disposition directement par GitHub <IconGithub class="list-success h-4 w-4 inline-flex"></IconGithub> et sont en général un bon terrain de départ pour composer vos propres Actions. Il existe aussi des Actions faites par des tiers certifiés <IconBadgeCheck class="list-success h-4 w-4 inline-flex"></IconBadgeCheck> par GitHub.

Dans notre cas, nous pouvons déduire que la troisième étape est une Action composée par WhyNotHugo, disponible dans son répo python-linting, sur la branche `master`.
