---
layout: post
title: Gatherer en Java
---

L'API des **Stream Gatherers** est une fonctionnalité apparu en Java 22 puis 
finalisé en Java 24 qui permet à l'utilisateur de créer ses propres
opérations intermédiaires.

## Utilisation

Tout comme la méthode `collect()` qui prend en paramètre un `Collector`
pour les opérations finales, il existe une méthode `gather()` qui prend un
en paramètre `Gatherer` pour les opérations intermédiaires.

Note : Pour savoir si une méthode est une opération intermédiaire,
on regarde si la méthode retourne un `Stream`.

Il existe deux façons de créer un Gatherer :
- `Gatherer.of()` qui prend une interface fonctionnelle `Integrator` en paramètre.
- La classe factory `Gatherers` qui contient des méthodes permettant de créer un Gatherer.

## Integrator

L'interface fonctionnelle `Integrator` contient une méthode `integrate()`
qui prend trois paramètres :
- `state`: Une variable d'état.
- `element`: L'élément courant qu'on va consommer.
- `downstream`: Un downstream qui permet de pousser un élément avec la méthode `push()`.

Et renvoie un boolean:
- `true`: Il reste des éléments à consommer.
- `false`: Il ne reste plus d'éléments à consommer.

Si on souhaite parcourir l'entièreté des éléments, on utilisera `Gatherer.Integrator.ofGreedy()`.

Pour ignorer un Stream parallèle, on utilisera `Gatherer.ofSequential()`.

### Exemples

Avec l'opération intermédiaire `map()`:
```java
var list = Stream.of("foo", "bar", "baz")
        .map(String::toUpperCase)
        .toList();
IO.println(list);
```
L'équivalent avec un `Gatherer`:
```java
var list = Stream.of("foo", "bar", "baz")
        .gather(Gatherer.of((state, element, downstream) -> {
            downstream.push(element.toUpperCase());
            return true;
        })).toList();
IO.println(list);
```
```shell
[FOO, BAR, BAZ]
```

## Gatherers

La classe factory `Gatherers` contient cinq méthodes prêt à l’emploi.

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
var list = Stream.of(1, 2, 3, 4, 5, 6, 7, 8, 9)
        .gather(Gatherers.scan(
                () -> "", (scanned, element) -> scanned + element))
        .toList();
IO.println(list);
```

```shell
[1, 12, 123, 1234, 12345, 123456, 1234567, 12345678, 123456789]
```

### mapConcurrent()

```java

```

```shell

```

### windowFixed()

```java
var list = Stream.of(1, 2, 3, 4, 5, 6, 7, 8, 9)
        .gather(Gatherers.windowFixed(3))
        .toList();
IO.println(list);
```

```shell
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

### windowSliding()

```java
var list = Stream.of(1, 2, 3, 4, 5, 6, 7, 8, 9)
        .gather(Gatherers.windowSliding(3))
        .toList();
IO.println(list);
```

```shell
[[1, 2, 3], [2, 3, 4], [3, 4, 5], [4, 5, 6], [5, 6, 7], [6, 7, 8], [7, 8, 9]]
```

## Sources:

* en:
  - [https://openjdk.org/jeps/485](https://openjdk.org/jeps/485)
  - [https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/stream/Gatherer.html](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/stream/Gatherer.html)
  - [https://dev.java/learn/api/streams/gatherers](https://dev.java/learn/api/streams/gatherers/)
  - [https://youtu.be/v_5SKpfkI2U?si=D4MqJi-3gRlvF8oU](https://youtu.be/v_5SKpfkI2U?si=D4MqJi-3gRlvF8oU)
  
* fr:
  - [https://blog.sciam.fr/2025/04/03/gatherers-java24.html](https://blog.sciam.fr/2025/04/03/gatherers-java24.html) 
  - [https://youtu.be/xp7TAq74uQQ?si=QPKpDyN1tkqygHcK](https://youtu.be/xp7TAq74uQQ?si=QPKpDyN1tkqygHcK)
