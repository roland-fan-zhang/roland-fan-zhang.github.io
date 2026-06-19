---
layout: post
title: C# code conventions
---

## Nommage

- Classes, méthodes, enums, champs/propriétés publics, namespaces : **PascalCase**
- Variables locales, paramètres : **camelCase**
- Champs/propriétés privés, protégés, internes : **_camelCase**
- Interfaces : commencent par **I**
- Fichiers : **PascalCase**, un par classe principale

## Organisation

**Modificateurs** : public, protected, internal, private, new, abstract, virtual, override, sealed, static, readonly, extern, unsafe, volatile, async

**Using** : au début, triés alphabétiquement (System d'abord)

**Membres de classe** :
1. Classes imbriquées, enums, délégués, événements
2. Static, const, readonly
3. Champs et propriétés
4. Constructeurs, finaliseurs
5. Méthodes

Puis par accès : public → internal → protected internal → protected → private

## Formatage

- **Indentation** : 2 espaces
- **Limite** : 100 caractères
- Une instruction par ligne
- Pas de saut avant accolade ouvrante
- Pas de saut entre accolade fermante et else
- Accolades obligatoires toujours
- Espace après if/for/while, virgules

## Code

- **Constantes** : const si possible, sinon readonly
- **Collections** : entrée type restrictif, sortie IList si transfert sinon restrictif
- **Array vs List** : List<> publique, arrays taille fixe
- **Propriétés** : expression body (=>) pour read-only une ligne
- **Lambdas** : méthode nommée si >2 statements ou réutilisé
- **var** : encouragé si type obvie
- **Extension methods** : rarement, source indisponible ou modification infaisable
- **Ref/out** : out pour retours seulement, ref très rare
- **LINQ** : appels simples, préférer extension methods
- **Structs** : presque toujours classe, sauf type valeur petit
- **Arguments** : constantes nommées, enums, variables intermédiaires, Named Arguments, configuration class

Sur l'IDE Rider, il faut modifier le fichier `.editorconfig` à la racine du projet.

Un exemple de `.editorconfig` : [https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/code-style-rule-options](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/code-style-rule-options)

Sur IntelliJ en Java, ce sera un fichier XML à fournir, par exemple : [https://google.github.io/styleguide/intellij-java-google-style.xml](https://google.github.io/styleguide/intellij-java-google-style.xml)

## Sources:

- [https://google.github.io/styleguide/csharp-style.html](https://google.github.io/styleguide/csharp-style.html)
- [https://google.github.io/styleguide/javaguide.html](https://google.github.io/styleguide/javaguide.html)
- [https://www.jetbrains.com/help/rider/Using_EditorConfig.html#what_is](https://www.jetbrains.com/help/rider/Using_EditorConfig.html)
- [https://www.jetbrains.com/help/idea/configuring-code-style.html#mewug_23](https://www.jetbrains.com/help/idea/configuring-code-style.html)