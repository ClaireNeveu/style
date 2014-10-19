## Formatting

The standard indention level is 3 and indentation should be done with spaces.
```
if (true) {
   val foo = ...
   ...
}
```

Brackets should only be used when a block is required. If the block can be replaced by a single expression, the single expression is preferred.

The following forms for `if` statements are acceptable:
```scala
if (cond)
   expressionOne
else
   expressionTwo

if (cond) expressionOne else expressionTwo
```

The "has type" operator `:` is always preceded and followed by one space.

## Modules

All type class definitions will take the following form:

In `lower-dirs/module/TypeClass.scala`:
```scala
package lower-modules.module

trait TypeClass[T] {
   def foo(t : T) : Int
   def bar : T
}

object Implicits {
   implicit class TypeClassOps[T : TypeClass](val t : T) extends AnyVal {
      def foo : Int = implicitly[TypeClass[T]].foo(t)
      def bar : T = implicitly[TypeClass[T]].bar
   }
}
```

In `lower-dirs/package.scala`:
```scala
package lower-modules

package object module {
   def foo[T : TypeClass](t : T) : Int = implicitly[TypeClass[T]].foo(t)
   def bar[T : TypeClass] : T = implicitly[TypeClass[T]].bar
}
```
