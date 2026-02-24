---
layout: post
title: What is a Gatherer
---

L'API des **Stream Gatherers** est une fonctionnalité apparu en Java 22 puis 
finalisé en Java 24 qui permet à l'utilisateur de créer ses propres
opérations intermédiaire.

Note: Pour savoir si une méthode est une opération intermédiaire, 
on regarde si la méthode retourne un **Stream**.

## Utilisation

Tout comme la méthode `collect()` qui prend en paramètre un `Collector`
pour les opérations finales, il existe une méthode `gather()` qui prend un
`Gatherer` en paramètre pour les opérations intermédiaires.

Il existe deux façons de créer un Gatherer:
- Avec une interface fonctionnelle `Integrator`
- Avec une classe factory `Gatherers`

## Integrator

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

### mapConcurrent()

### windowFixed()

### windowSliding()


## Sources:

* en:
  - [https://openjdk.org/jeps/485](https://openjdk.org/jeps/485)
  - [https://www.baeldung.com/java-stream-gatherers](https://youtu.be/__piR-N9pXA?si=TaEXEtX5DwwLXNQw)
  - [https://dev.java/learn/api/streams/gatherers](https://dev.java/learn/api/streams/gatherers/)
  - [https://www.youtube.com/watch?v=v_5SKpfkI2U](https://www.youtube.com/watch?v=v_5SKpfkI2U)
  
* fr:
  - [https://blog.sciam.fr/2025/04/03/gatherers-java24.html](https://blog.sciam.fr/2025/04/03/gatherers-java24.html) 
  - [https://www.youtube.com/watch?v=__piR-N9pXA](https://www.youtube.com/watch?v=__piR-N9pXA)