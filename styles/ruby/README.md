Ruby
====

[Sample](sample.rb)

* Avoid conditional modifiers (lines that end with conditionals). - PUNTED
* Avoid multiple assignments per line (`one, two = 1, 2`).
* Avoid organizational comments (`# Validations`).
* Avoid ternary operators (`boolean ? true : false`). Use multi-line `if`
  instead to emphasize code branches.
* Avoid explicit return statements. - PUNTED
* Avoid using semicolons.
* Don't use `self` explicitly anywhere except class methods (`def self.method`)
  and assignments (`self.attribute =`).
* Prefer nested class and module definitions over the shorthand version
  [Example][class definition example]
* Prefer `detect` over `find`.
* Prefer `select` over `find_all`.
* Prefer `map` over `collect`.
* Prefer `reduce` over `inject`.
* Prefer single quotes for strings unless more readable
* Prefer `&&` and `||` over `and` and `or`.
* Prefer `!` over `not`.
* Prefer `&:method_name` to `{ |item| item.method_name }` for simple method
  calls.
* Prefer `if` over `unless`.
* Use `_` for unused block parameters.
* Use `{...}` for single-line blocks. Use `do..end` for multi-line blocks.
* Avoid chaining blocks of code.
* Use `{...}` for multi-line blocks that are chained.
* Use `?` suffix for predicate methods.
* Use `CamelCase` for classes and modules, `snake_case` for variables and
  methods, `SCREAMING_SNAKE_CASE` for constants.
* Use `def self.method`, not `def Class.method` or `class << self`.
* Don't use spaces after required keyword arguments. [Example][required kwargs]
* Use `each`, not `for`, for iteration.
* Use heredocs for multi-line strings.
* User `private` for non-public `attr_reader`s, `attr_writer`s, and `attr_accessor`s.
* Order class methods above instance methods.
* Alphabetize your Gemfile based upon sections.
* Order methods by concern.

[trailing comma example]: /style/ruby/sample.rb#L57
[required kwargs]: /style/ruby/sample.rb#L24
[class definition example]: /style/ruby/sample.rb#L121
