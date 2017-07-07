---
layout: post
title: set-err_out-equal-to-std_out.md
author: Baptiste
tags: [bash]
---
Quand on écrit une commande, on peut en rediriger la sortie standard vers un fichier : `commande > file` ou à la fin d'un fichier : `commande >> file`

Si on souhaite en plus logger dans ce fichier les erreurs de `commande`, faire ceci : `commande > file 2>&1`. Le flux 1 est le standard, le flux 2 est l'erreur, et `2>&1` renvoie 2 vers le pointeur de 1.

Particulièrement utile pour une commande cron qui peut être amenée à bugger, cas où c'est le seul moyen de voir l'output d'erreur.
