---
layout: post
title: C# code conventions
---

La convention est la suivante :

```csharp
using System;

namespace MyNamespace {
  public interface IMyInterface {
    public int Calculate(float value, float exp);
  }

  public enum MyEnum {
    Yes,
    No,
  }

  public class MyClass {
    public int Foo = 0;
    public bool NoCounting = false;
    private class Results {
      public int NumNegativeResults = 0;
      public int NumPositiveResults = 0;
    }
    private Results _results;
    public static int NumTimesCalled = 0;
    private const int _bar = 100;
    private int[] _someTable = {
      2, 3, 4,
    };

    public MyClass() {
      _results = new Results {
        NumNegativeResults = 1,
        NumPositiveResults = 1,
      };
    }

    public int CalculateValue(int mulNumber) {
      var resultValue = Foo * mulNumber;
      NumTimesCalled++;
      Foo += _bar;

      if (!NoCounting) {
        if (resultValue < 0) {
          _results.NumNegativeResults++;
        } else if (resultValue > 0) {
          _results.NumPositiveResults++;
        }
      }

      return resultValue;
    }

    public void ExpressionBodies() {
      Func<int, int> increment = x => x + 1;

      Func<int, int, long> difference1 = (x, y) => {
        long diff = (long)x - y;
        return diff >= 0 ? diff : -diff;
      };

      Func<int, int, long> difference2 =
          (x, y) => {
            long diff = (long)x - y;
            return diff >= 0 ? diff : -diff;
          };

      CallWithDelegate(
          (x, y) => {
            long diff = (long)x - y;
            return diff >= 0 ? diff : -diff;
          });
    }

    void DoNothing() {}

    void AVeryLongFunctionNameThatCausesLineWrappingProblems(int longArgumentName,
                                                             int p1, int p2) {}

    void AnotherLongFunctionNameThatCausesLineWrappingProblems(
        int longArgumentName, int longArgumentName2, int longArgumentName3) {}

    void CallingLongFunctionName() {
      int veryLongArgumentName = 1234;
      int shortArg = 1;
      AnotherLongFunctionNameThatCausesLineWrappingProblems(shortArg, shortArg,
                                                            veryLongArgumentName);
      AnotherLongFunctionNameThatCausesLineWrappingProblems(
          veryLongArgumentName, veryLongArgumentName, veryLongArgumentName);
    }
  }
}
```

Sur l'IDE Rider, il faut modifier le fichier `.editorconfig` à la racine du projet.

Un exemple de `.editorconfig` : https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/code-style-rule-options

Sur IntelliJ en Java, ce sera un fichier XML à fournir, par exemple : https://google.github.io/styleguide/intellij-java-google-style.xml

## Sources:

- [https://google.github.io/styleguide/csharp-style.html](https://google.github.io/styleguide/csharp-style.html)
- [https://google.github.io/styleguide/javaguide.html](https://google.github.io/styleguide/javaguide.html)
- [https://www.jetbrains.com/help/rider/Using_EditorConfig.html#what_is](https://www.jetbrains.com/help/rider/Using_EditorConfig.html)
- [https://www.jetbrains.com/help/idea/configuring-code-style.html#mewug_23](https://www.jetbrains.com/help/idea/configuring-code-style.html)