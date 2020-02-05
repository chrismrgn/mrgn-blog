---
title: "Creating Copies of your Database with PowerShell"
date: 2016-06-23T17:32:38.000Z
description: 
featuredpost: false
tags: 
  - PowerShell
  - PowerShell
  - SDL Web (SDL Tridion)
  - SDL Web 8

---

Recently, while developing a migration script, I needed to repeatedly test against a clean base version of my Content Manager database (before migration).

The easiest way to do this was to create a number of identical clones of the base database, and then update the SDL Tridion configuration each time I needed a fresh one.

Cloning the database over and over, chaning names and file paths was time consuming, so I created a small PowerShell script to help

\[gist id="3b1a9c5d39e49edac90aa6a59b0c488b" file="CreateClonesOfDatabase.ps1"\]
