# Kevin Le - Gradual Typing in Programming Languages

## **Questions**

The LLMs were prompted to give more detailed answers to the following questions (e.g., using "Dive deeper into these points")[^1].

- What is the history of gradual typing?
- Which programming languages have gradual typing, and how has it affected their usage?
- How does gradual typing influence software maintainability and developer productivity?
- What are the trade-offs between static typing, dynamic typing, and gradual typing in terms of space/time complexity and runtime performance?
- How have recent advancements in type inference improved gradual typing systems?

[^1]: Claude Sonnet 3.5 expanded on more technical details of how each mentioned programming language implemented gradual programming. This detracted from understanding the main purpose of gradual programming, which is why it was excluded from this literature review.

## **Concepts**

- Static Data Type: Defined during compile time and cannot change during runtime. This behavior is because of static type checking.
- Dynamic Data Type: Allows variables to change their data type during runtime.

## **References**
- BairesDev Editorial Team [Difference Between Static and Dynamic Data Types](https://www.bairesdev.com/blog/static-vs-dynamic-typing/)
- Jeremy Siek and Walid Taha (2006). [*Gradual Typing for Functional Languages*](http://scheme2006.cs.uchicago.edu/13-siek.pdf)
- Sam Tobin-Hochstadt and Matthias Felleisen (2010). [*Logical Types for Untyped Languages*](https://www2.ccs.neu.edu/racket/pubs/icfp10-thf.pdf)
- Guido van Rossum, Jukka Lehtosalo, Łukasz Langa (2014). [PEP 484: Type Hints for Python](https://peps.python.org/pep-0484/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html) (See section for `any` type)
- Ben Greenman and Matthias Felleisen. 2018. [A Spectrum of Type Soundness and Performance](https://www2.ccs.neu.edu/racket/pubs/icfp18-gf.pdf). Proc. ACM Program. Lang. 2, ICFP, Article 71 (September 2018), 31 pages. https://doi.org/10.1145/3236766

## **Introduction**
Gradual typing is to mix static and dynamic data typing in the same codebase. Doing this ensures data type safety and flexibility. This literature review investigates the performance and reliability of gradual typing in modern programming languages, such as TypeScript, Python, and many others.

## **Synthesized Conversation Using GPT-4o and Claude Sonnet 3.5**

1. **Historical Background**

Before gradual typing, the field was divided into two camps: statically typed languages, which prioritized early error detection, and dynamically typed languages, which emphasized flexibility. Languages like JavaScript, Ruby, and Python began as dynamically typed, prioritizing rapid development cycles over static type safety. 

Gradual typing emerged in the mid-2000s as a way to combine the benefits of both static and dynamic typing. The concept was introduced by Jeremy Siek and Walid Taha in their 2006 paper *Gradual Typing for Functional Languages*. The motivation was to offer flexibility, allowing developers to start with dynamic typing and introduce static types incrementally. Their research showed that gradual typing could be integrated into functional languages, but its principles have since been adopted by object-oriented and scripting languages. Other notable contributors include Sam Tobin-Hochstadt and Matthias Felleisen, who extended the theory of gradual typing to object-oriented programming languages through their work on Typed Racket. In Python, the introduction of PEP 484 by Guido van Rossum and the ongoing development of the `mypy` type checker have popularized type hints. This hybrid typing system gained popularity as dynamically typed languages like JavaScript and Python provided a way to introduce static types for added reliability without losing flexibility. 

Key milestones in its development include:
- 2006: Introduction of gradual typing concept
- 2008: Formalization of gradual typing for object-oriented languages
- 2010s: Adoption by mainstream programming languages

### Detailed History of Gradual Typing

#### Early Foundations (2000-2006)
- The groundwork for gradual typing was laid by research into combining static and dynamic typing.
- In 2002, Strongtalk, an optional type system for Smalltalk, was released, showcasing early ideas of mixing static and dynamic typing.
- 2002: "Combining Static and Dynamic Typing in Ruby" by Michael Furr et al. explored early ideas of mixing typing disciplines.

#### Introduction and Formalization (2006-2010)
- 2006: Jeremy Siek and Walid Taha publish "Gradual Typing for Functional Languages," coining the term "gradual typing."
- 2007: Siek and Taha, along with Tariq Zidan, extend the concept to object-oriented languages in "Gradual Typing for Objects."
- 2008: Formalization of gradual typing for object-oriented languages by Siek and Taha in "Gradual Typing for Objects, Revisited."
- 2009: "Well-typed Programs Can't Be Blamed" by Philip Wadler and Robert Bruce Findler introduces the blame calculus.

#### Mainstream Adoption and Research (2010-2015)
- 2011: "Like Types for Untyped Languages" by Tobias Wrigstad et al. introduces like types, a precursor to gradual typing in Lua.
- 2012: TypeScript is released by Microsoft, bringing gradual typing to the JavaScript ecosystem.
- 2014: Dart language (by Google) adopts optional static typing.
- 2014: Facebook releases Hack, a gradually typed dialect of PHP.
- 2014: "Is Sound Gradual Typing Dead?" by Asumu Takikawa et al. raises important questions about performance.

#### Maturation and Widespread Use (2015-Present)
- 2015: Python introduces type hints with PEP 484, adopting a form of gradual typing.
- 2016: PHP 7 introduces scalar type declarations and return type declarations.
- 2017: "Theorems for Free for Free: Parametricity, With and Without Types" by Amal Ahmed et al. explores parametricity in the context of gradual typing.
- 2018: Mypy, a static type checker for Python, reaches version 0.600, marking increased adoption of gradual typing in the Python community.
- 2020: "The Gradualizer: A Methodology and Algorithm for Generating Gradual Type Systems" by Matteo Cimini and Jeremy G. Siek presents a systematic approach to creating gradually typed languages.

2. **Key Languages Adopting Gradual Typing**

Several programming languages have incorporated gradual typing:

- TypeScript: A gradually typed superset of JavaScript; enforces type safety while maintaining compatibility with JavaScript
- Python: Introduced optional type hints in version 3.5 (PEP 484)
- Reticulated Python: A research implementation of gradual typing for Python
- PHP: Added type declarations starting with PHP 7
- Hack: Facebook's gradually typed dialect of PHP
- Dart: Supports optional static typing

The adoption of gradual typing has generally increased the usage and popularity of these languages, especially in large-scale projects. TypeScript, for example, has seen widespread adoption in the JavaScript ecosystem due to its gradual typing features.

3. **Subfields of PL**

The development of gradual typing required collaboration between type theory and compiler optimization techniques, and from subfields related to type inference and type soundness (software correctness). Researchers have explored how to build type systems that can accommodate both static and dynamic checks without sacrificing efficiency. Advances in compiler design have also been critical, particularly in optimizing the runtime performance of gradually typed languages. Additionally, gradual typing interacts with subfields like runtime verification and program analysis, where dynamic type checks need to be efficient.

4. **Performance Comparison between Static, Dynamic, and Gradual Typing**
   
Gradual typing introduces runtime overhead due to type checks between static and dynamic sections. Recent research focuses on optimizing these checks and enhancing type inference algorithms to mitigate performance issues.

Space/Time Complexity:
- Static typing: Generally lowest runtime overhead
- Dynamic typing: Higher runtime overhead due to dynamic type checks
- Gradual typing: Can have overhead between static and dynamic, depending on implementation

Runtime Performance:
- Static typing: Usually offers the best performance due to compile-time optimizations
- Dynamic typing: Often slower due to runtime type checks and less opportunity for optimization
- Gradual typing: Performance can vary; typed portions can be optimized, while untyped portions retain flexibility

Let's examine some specific scenarios and benchmarks:

a) Space/Time Complexity:
- Static Typing: C++ programs typically have the lowest memory footprint and fastest execution.
- Dynamic Typing: Python programs often use more memory due to dynamic dispatch and boxing of primitive types.
- Gradual Typing: TypeScript compiled to JavaScript performs similarly to plain JavaScript, while gradually typed Python with runtime checks can be slower.

b) Runtime Performance:
- The Computer Language Benchmarks Game provides comparisons:
  - Static languages like C and Rust consistently outperform dynamic languages.
  - JIT-compiled languages like Java often bridge the gap.
  - Gradually typed languages vary; TypeScript performs similarly to JavaScript, while gradual typing in Python can introduce overhead.

c) Developer Experience:
- Static Typing: Languages like Rust provide strong guarantees but have a steeper learning curve.
- Dynamic Typing: Languages like Ruby offer rapid prototyping capabilities but may lead to more runtime errors.
- Gradual Typing: TypeScript allows developers to incrementally add types, balancing flexibility and safety.

5. **Developer Experience and Code Maintainability**
   
Gradual typing enhances code maintainability, allowing developers to introduce types progressively as projects grow. However, managing the interaction between dynamic and static types can add complexity. 

Gradual typing can significantly impact software maintainability and developer productivity:

Advantages:
- Improved code readability and self-documentation
- Better tooling support (e.g., autocompletion, refactoring)
- Earlier detection of certain types of errors
- Easier onboarding for new developers

Potential challenges:
- Learning curve for developers used to purely dynamic typing
- Overhead of adding and maintaining type annotations
- Potential for false sense of security if type checking is incomplete

Let's explore some concrete examples and studies:

a) Case Studies:
- Airbnb's migration to TypeScript: Reported significant reduction in production incidents related to type errors.
- Google's use of type annotations in Python: Found that adding type annotations to 35% of code caught 24% of bugs in production.

b) Tooling Improvements:
- IDEs like Visual Studio Code and PyCharm leverage type information for enhanced refactoring capabilities.
- Static analysis tools like ESLint and Pyflakes can provide more accurate warnings with type information.

c) Documentation Benefits:
- Type annotations serve as a form of always-up-to-date documentation.
- Tools like Sphinx for Python can generate API documentation automatically from type hints.

d) Learning Curve Considerations:
- Initial productivity may decrease as developers learn the type system.
- Long-term productivity often increases, especially in larger codebases.

e) Performance Impact:
- Some gradual typing implementations (e.g., TypeScript) have no runtime overhead.
- Others (e.g., Python's runtime type checking) can introduce performance penalties.

Overall, gradual typing tends to improve maintainability and productivity, especially in larger codebases and teams.

6. **Recent Research Trends**
   
Recent trends in gradual typing include improvements in type inference algorithms, reducing the cognitive load for developers when transitioning from dynamic to static typing. Researchers are also investigating ways to optimize runtime type checks through static analysis techniques. For example, Just-In-Time (JIT) compilers are being designed to perform type checks more efficiently, reducing the runtime performance overhead often associated with gradual typing systems.

Research on compiler optimizations for reducing runtime type checks' performance cost is ongoing. A relevant paper is [*Safe & Efficient Gradual Typing for TypeScript*](https://goto.ucsd.edu/~pvekris/docs/safets.pdf) by Rastogi et al., which focuses on optimizing type checking in large-scale systems.

Recent advancements in type inference have improved gradual typing systems:

- Flow-sensitive type inference: Analyzes control flow to infer more precise types
- Shape analysis: Infers structural types for objects based on their usage
- Machine learning-based type inference: Uses ML models to predict likely types
- Incremental type checking: Efficiently rechecks only changed portions of code
- Intersection and union types: Allows more expressive type annotations

- Let's explore these advancements with more technical detail:

a) Flow-sensitive type inference:
- Technique: Analyzes control flow to refine types within different branches.
- Example in TypeScript:
  ```typescript
  function example(x: string | number) {
    if (typeof x === "string") {
      console.log(x.toUpperCase());  // x is inferred as string here
    } else {
      console.log(x.toFixed(2));     // x is inferred as number here
    }
  }
  ```

b) Shape analysis:
- Technique: Infers structural types based on object usage.
- Example in Python with mypy:
  ```python
  from typing import TypedDict

  class Point(TypedDict):
      x: float
      y: float

  def distance(p: Point) -> float:
      return (p['x']**2 + p['y']**2)**0.5
  ```

c) Machine learning-based type inference:
- Technique: Uses ML models trained on large codebases to predict types.
- Example: Microsoft's TypeScript team is experimenting with ML models to suggest more accurate types in complex scenarios.

d) Incremental type checking:
- Technique: Only rechecks changed portions of code and their dependencies.
- Example: Flow's incremental mode, which significantly speeds up type checking in large projects.

e) Intersection and union types:
- Technique: Allows more expressive type combinations.
- Example in TypeScript:
  ```typescript
  type Serializable = string | number | boolean | null | undefined;
  type SerializableArray = Serializable[];

  function process(input: SerializableArray & { length: 5 }) {
    // input is an array of serializable values with exactly 5 elements
  }
  ```

f) Gradual typing with blame:
- Technique: Tracks the origin of type errors in mixed typed/untyped code.
- Example: Reticulated Python's implementation assigns blame to either typed or untyped code regions when runtime type errors occur.

g) Optional and nullable types:
- Technique: Explicitly represents the presence or absence of a value.
- Example in Kotlin:
  ```kotlin
  fun strlen(s: String?): Int = s?.length ?: 0
  ```

These advancements continue to push the boundaries of what's possible with gradual typing, making it an increasingly attractive option for large-scale software development. Gradual typing systems more powerful and user-friendly, reducing the annotation burden on developers while providing stronger type guarantees.

## Key Researchers and Contributors
- Jeremy Siek, Walid Taha, and Philip Wadler have been instrumental in developing the theoretical foundations.
- Anders Hejlsberg led the development of TypeScript at Microsoft.
- Guido van Rossum and Jukka Lehtosalo drove the adoption of type hints in Python.
- Sam Tobin-Hochstadt and Matthias Felleisen contributed significantly to gradual typing theory and practice.

The evolution of gradual typing represents a significant shift in programming language design, bridging the gap between static and dynamic typing paradigms. Recent research focuses on performance optimization, type inference improvements, and formal guarantees for gradually typed programs.
