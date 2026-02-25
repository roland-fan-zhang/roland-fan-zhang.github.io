---
layout: post
title: What is a Gatherer
---

L'API des **Stream Gatherers** est une fonctionnalité apparu en Java 22 puis 
finalisé en Java 24 qui permet à l'utilisateur de créer ses propres
opérations intermédiaire.

## Utilisation

Tout comme la méthode `collect()` qui prend en paramètre un `Collector`
pour les opérations finales, il existe une méthode `gather()` qui prend un
en paramètre `Gatherer` pour les opérations intermédiaires.

Note: Pour savoir si une méthode est une opération intermédiaire,
on regarde si la méthode retourne un `Stream`.

Il existe deux façons de créer un Gatherer:
- `Gatherer.of()` qui prend une interface fonctionnelle `Integrator` en paramètre.
- La classe factory `Gatherers` qui contient des méthodes permettant de créer un Gatherer.

## Integrator

L'interface fonctionnelle `Integrator` contient une méthode `integrate()`
qui prend trois paramètres:
- `state`: Une variable d'état.
- `element`: L'élément courant qu'on va consommer.
- `downstream`: Un downstream qui permet de pousser un élément avec la méthode `push()`.

Et renvoie un boolean:
- `true`: Il reste des éléments à consommer.
- `false`: Il ne reste plus d'éléments à consommer.

Si on souhaite parcourir l'entièreté des éléments, on utilisera `Gatherer.Integrator.ofGreedy()`

### Exemples

```java

```

## Gatherers

### fold()
```java
var list = Stream.of("foo", "bar", "baz")
        .gather(Gatherers.fold(
            () -> "", (s1, s2) -> s1 + s2))
        .toList();
IO.println(list);
```

```shell
[foobarbaz]
```

### scan()

```java

```

```shell

```

### mapConcurrent()

```java

```

```shell

```

### windowFixed()

```java

```

```shell

```

### windowSliding()

```java

```

```shell

```

## Sources:

* en:
  - [https://openjdk.org/jeps/485](https://openjdk.org/jeps/485)
  - [https://dev.java/learn/api/streams/gatherers](https://dev.java/learn/api/streams/gatherers/)
  - [https://youtu.be/v_5SKpfkI2U?si=D4MqJi-3gRlvF8oU](https://youtu.be/v_5SKpfkI2U?si=D4MqJi-3gRlvF8oU)
  
* fr:
  - [https://blog.sciam.fr/2025/04/03/gatherers-java24.html](https://blog.sciam.fr/2025/04/03/gatherers-java24.html) 
  - [https://youtu.be/xp7TAq74uQQ?si=QPKpDyN1tkqygHcK](https://youtu.be/xp7TAq74uQQ?si=QPKpDyN1tkqygHcK)