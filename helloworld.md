---
title: Run Scala and Typescript code in articles
date: 2019-03-21
---

Powered by [Typescript Service](https://github.com/Microsoft/TypeScript/) and [Scastie](https://scastie.scala-lang.org/), GitPress supports Markdown extension for Scala and Typescript. 

You could enable this feature using Markdown's code block syntax.

Check the [source of this post](https://github.com/gitpress-io/blog/blob/master/source/scala-and-typescript.md) to learn how to use them.

## Scala

```scala
def sayHello(person: String): Unit = {
  println("Hello, " + person)
}
sayHello("Ada")
```

## Typescript

```typescript
function sayHello(person: string) {
  console.log("Hello, " + person);
}
sayHello("Ada");
```

