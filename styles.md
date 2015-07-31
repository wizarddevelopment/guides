# ERb

* When wrapping long lines, keep the method name on the same line as the ERb
  interpolation operator and keep each method argument on its own line.
* Prefer double quotes for attributes.

```erb
<%= short_method_call_that_fits_on_one_line arguments %>

<%= link_to(
  some_object_with_a_long_name.title,
  parent_object_child_object_path(some_object_with_a_long_name)
) %>
```

# Git

* Avoid merge commits by using a rebase workflow.
* Squash multiple trivial commits into a single commit.
* Write a [good commit message].
* Title branches as (feature/bug/chore/style)/(branch name)

[good commit message]: http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html

## Submitting Pull Requests

* Have descriptive commit messages
* Submit pull requests with a clear and concise title
* Use `-` for points
* Include a screen shot if any styles have changed
* Include a link to the card that the PR covers

# HTML

* Prefer double quotes for attributes.


# JavaScript

* Prefer ES6 classes over prototypes.
* Use strict equality checks (`===` and `!==`) except when comparing against
  (`null` or `undefined`).
* Prefer [arrow functions] `=>`, over the `function` keyword except when
  defining classes or methods.
* Use semicolons at the end of each statement.
* Prefer double quotes.
* Two spaces
* Use `PascalCase` for classes, `lowerCamelCase` for variables and functions,
  `SCREAMING_SNAKE_CASE` for constants, `_singleLeadingUnderscore` for private
  variables and functions.
* Prefer [template strings] over string concatenation.
* Prefer promises over callbacks.
* Prefer array functions like `map` and `forEach` over `for` loops.

[template strings]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/template_strings
[arrow functions]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions


```js
object = { spacing: true }

class Cat {
  canBark() {
    return false;
  }
}
```

# Rails

* *UNDECIDED* Avoid `member` and `collection` routes.
* Use private instead of protected when defining controller methods.
* Name date columns with `_on` suffixes.
* Name datetime columns with `_at` suffixes.
* Name time columns (referring to a time of day with no date) with `_time`
  suffixes.
* Name initializers for their gem name.
* Order ActiveRecord associations alphabetically by association type, then
  attribute name.
* Order ActiveRecord validations alphabetically by attribute name.
* Order ActiveRecord associations above ActiveRecord validations.
* Order controller contents: filters, public methods, private methods.
* Order i18n translations alphabetically by key name.
* Order model contents: constants, macros, public methods, private methods.
* Put application-wide partials in the [`app/views/application`] directory.
* Use scope rather than class methods for associations.
* Don't use default scopes.
* Use the default `render 'partial'` syntax over `render partial: 'partial'`.
* *UNDECIDED* Use `link_to` for GET requests, and `button_to` for other HTTP verbs.

[`app/views/application`]: http://asciicasts.com/episodes/269-template-inheritance

## Migrations

* Required fields should always be not null.
* Foreign key constraints should always exist for related records.
* Set an empty string as the default constraint for non-required string and text.
  fields.

```ruby
class CreateClearanceUsers < ActiveRecord::Migration
  def change
    create_table :users  do |t|
      t.timestamps null: false
      t.string :email, null: false
      t.string :name, null: false, default: ''
    end

    add_index :users, :email
  end
end
```

## Routes

* Use the `:only` option to explicitly state exposed routes.
* Avoid the `:except` option in routes.
* Order resourceful routes alphabetically by name.

## Delay Jobs

* Define a `PRIORITY` constant at the top of delayed job classes.
* Define two public methods: `self.enqueue` and `perform`.
* Put delayed job classes in `app/jobs`.

## Email

* Use the user's name in the `From` header and email in the `Reply-To` when.
  [delivering email on behalf of the app's users].

[delivering email on behalf of the app's users]: http://robots.thoughtbot.com/post/3215611590/recipe-delivering-email-on-behalf-of-users


# Ruby

* *UNDECIDED* Avoid conditional modifiers (lines that end with conditionals).
* Avoid multiple assignments per line (`one, two = 1, 2`).
* Avoid organizational comments (`# Validations`).
* Avoid ternary operators (`boolean ? true : false`). Use multi-line `if`
  instead to emphasize code branches.
* Avoid explicit return statements. - PUNTED
* Avoid using semicolons.
* Don't use `self` explicitly anywhere except class methods (`def self.method`)
  and assignments (`self.attribute =`).
* Prefer nested class and module definitions over the shorthand version
* Prefer `detect` over `find`.
* Prefer `select` over `find_all`.
* Prefer `map` over `collect`.
* Prefer `reduce` over `inject`.
* Prefer double quotes over single
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
* Don't use spaces after required keyword arguments.
* Use `each`, not `for`, for iteration.
* Use heredocs for multi-line strings.
* User `private` for non-public `attr_reader`s, `attr_writer`s, and `attr_accessor`s.
* Order class methods above instance methods.
* Alphabetize your Gemfile based upon sections.
* Order methods by concern.

```ruby
class SomeClass
  SOME_CONSTANT = "upper case name"

  def initialize(attributes)
    @some_attribute = attributes[:some_attribute]
    @another_attribute = attributes[:another_attribute]
    @user_factory = attributes[:user_factory]
  end

  def method_with_arguments(argument_one, argument_two)
    a_really_long_line_that_is_broken_up_over_multiple_lines_and.
      subsequent_lines_are_indented_and.
      each_method_lives_on_its_own_line
  end

  def method_with_long_signature(
    the_first_arg:,
    the_second_one:,
    and_another_one:
  )
    # code here
  end

  def method_with_required_keyword_arguments(one:, two:)
  end

  def method_with_multiline_block
    some_method_before_block(should_be_followed_by_a_newline)

    items.each do |item|
      do_something_with_item
      perform_another_action
    end

    some_method_after_block(should_follow_after_newline)
  end

  def method_with_single_method_block
    items.map(&:some_attribute)
  end

  def method_with_oneline_combined_methods_block
    items.map { |item| "#{item.one} #{item.two}" }
  end

  def method_that_returns_an_array
    [item_one, item_two]
  end

  def method_that_returns_a_hash
    { :key => "value" }
  end

  def method_with_large_hash
    {
      :one => "value",
      :two => "value",
    }
  end

  def method_with_large_array
    [
      :one,
      :two,
      :three,
    ]
  end

  def invoke_method_with_arguments_on_multiple_lines
    some_method(
      i_am_a_long_variable_name_that_will_never_fit_on_one_line_with_others,
      two,
      three
    )

    # Bad:
    some_method(one,
                two)
  end

  def method_which_uses_infix_operators
    left + middle - right
  end

  def method_which_uses_unary_operator
    !signed_in?
  end

  def method_without_arguments
    if complex_condition?
      positive_branch
    else
      negative_branch
    end

    rest_of_body
  end

  def method_that_uses_factory
    user = @user_factory.new
    user.ensure_authenticated!
  end

  def self.class_method
    method_body
  end

  protected

  attr_reader :foo
  attr_accessor :bar
  attr_writer :baz

  private

  def complex_condition?
    part_one? && part_two?
  end
end

module A
  class B
  end
end

```

# Sass

## Formatting

* Use the SCSS syntax.
* Use hyphens when naming mixins, extends, classes, functions & variables: `span-columns` not `span_columns` or `spanColumns`.
* Use one space between property and value: `width: 20px` not `width:20px`.
* Use a blank line above a selector that has styles.
* Prefer hex color codes `#fff` or `#FFF`.
* Avoid using shorthand properties for only one value: `background-color: #ff0000;`, not `background: #ff0000;`
* Use `//` for comment blocks not `/* */`.
* Use one space between selector and `{`.
* Use double quotation marks.
* Use only lowercase, except for hex or string values.
* Don't add a unit specification after `0` values, unless required by a mixin.
* Use a leading zero in decimal numbers: `0.5` not `.5`
* Use space around operands: `$variable * 1.5`, not `$variable*1.5`
* Avoid in-line operations in shorthand declarations (Ex. `padding: $variable * 1.5 variable * 2`)
* Use parentheses around individual operations in shorthand declarations: `padding: ($variable * 1.5) ($variable * 2);`
* Use double colons for pseudo-elements
* Use a `%` unit for the amount/weight when using Sass's color functions: `darken($color, 20%)`, not `darken($color, 20)`

## Order

* Use alphabetical order for declarations.
* Place `@extends` and `@includes` at the top of your declaration list.
* Place media queries directly after the declaration list.
* Place concatenated selectors second.
* Place pseudo-states and pseudo-elements third.
* Place nested elements fourth.
* Place nested classes fifth.

## Selectors

* Don't use ID's for style.
* Use meaningful names: `$visual-grid-color` not `$color` or `$vslgrd-clr`.
* Use ID and class names that are as short as possible but as long as necessary.
* Avoid using the direct descendant selector `>`.
* Avoid nesting more than 4 selectors deep.
* Don't nest more than 6 selectors deep.
* Use HTML tags on vague classes that need a qualifier like `header.application` not `.main`.
* Avoid using the HTML tag in the class name: `section.news` not `section.news-section`.
* Avoid using HTML tags on classes for generic markup `<div>`, `<span>`: `.widgets` not `div.widgets`.
* Avoid using HTML tags on classes with specific class names like `.featured-articles`.
* Avoid using comma delimited selectors.
* Avoid nesting within a media query.

## Organization

* Use Bourbon for a Sass library.
* Use Neat for a grid framework.
* Use Bitters/`base` directory for styling element selectors, global variables, global extends and global mixins.
* Use [Normalize](https://github.com/necolas/normalize.css) for browser rendering consistency, rather than a reset.
* Use HTML structure for ordering of selectors. Don't just put styles at the bottom of the Sass file.
* Avoid having files longer than 100 lines.


```sass
@import "bourbon";

.featured-article {
  @include mixin;
  attribute: value;

  @include media(value) {
    attribute: value;
  }

  &.additional-selector {
    attribute: value;
  }

  &:hover {
    attribute: value;
  }

  &::before {
    content: "<";
  }

  &::after {
    content: ">";
  }

  h1 {
    attribute: value;
  }

  .news {
    attribute: value;
    attribute: ($variable * 1.5) 2em;

    article {
      @extend media(value) {
        attribute: value;
      }

      p {
        attribute: value;
      }
    }
  }

  .sidebar {
    attribute: value;

    h2 {
      attribute: value;
    }
  }
}
```

# Testing

* Avoid the `private` keyword in specs.
* Avoid checking boolean equality directly. Instead, write predicate methods and
  use appropriate matchers.

```ruby
# Class under test:
class Thing
  def awesome?
    true
  end
end

# RSpec test:
describe Thing, "#awesome?" do
  it "is true" do
    thing = Thing.new
    expect(thing).to be_awesome
  end
end
```

* Prefer `eq` to `==` in RSpec.
* Separate setup, exercise, verification, and teardown phases with newlines.
* Use RSpec's [`expect` syntax].
* Use RSpec's [`allow` syntax] for method stubs.
* Use `not_to` instead of `to_not` in RSpec expectations.
* Prefer the `have_css` matcher to the `have_selector` matcher in Capybara assertions.

[`expect` syntax]: http://myronmars.to/n/dev-blog/2012/06/rspecs-new-expectation-syntax
[`allow` syntax]: https://github.com/rspec/rspec-mocks#method-stubs

## UNDECIDED Acceptance Tests

* Avoid scenario titles that add no information, such as "successfully."
* Avoid scenario titles that repeat the feature title.
* Place helper methods for feature specs directly in a top-level `Features`
  module.
* Use Capybara's `feature/scenario` DSL.
* Use names like `ROLE_ACTION_spec.rb`, such as
  `user_changes_password_spec.rb`, for feature spec file names.
* Use only one `feature` block per feature spec file.
* Use scenario titles that describe the success and failure paths.
* Use spec/features directory to store feature specs.
* Use spec/support/features for support code related to feature specs.

```ruby
# spec/features/user_signing_up_spec.rb
require 'spec_helper'

feature 'User signing up' do
  scenario 'with valid email and password' do
    visit sign_up_path

    within '#sign_up' do
      fill_in 'Email', with: 'user@example.com'
      fill_in 'Password', with: 'Examp1ePa$$'
      click_button 'Sign up'
    end

    expect(page).to have_content('Sign out')
  end
end
```

## Factories
* Order `factories.rb` contents: sequences, traits, factory definitions.
* Order factory attributes: implicit attributes, explicit attributes,
  child factory definitions. Each section's attributes are alphabetical.
* Order factory definitions alphabetically by factory name.
* Use one factories.rb file per project.

## Unit Tests

* Don't prefix `it` block descriptions with `should`. Use [Imperative mood]
  instead.
* Use `subject` blocks to define objects for use in one-line specs.
* Put one-liner specs at the beginning of the outer `describe` blocks.
* Use `.method` to describe class methods and `#method` to describe instance
  methods.
* Use `context` to describe testing preconditions.
* Use `describe '#method_name'` to group tests by method-under-test
* Use a single, top-level `describe ClassName` block.
* Order validation, association, and method tests in the same order that they
  appear in the class.

[Imperative mood]: http://en.wikipedia.org/wiki/Imperative_mood

```ruby
describe SomeClass do
  context "when defining a subject" do
    # GOOD
    # it's okay to define a `subject` here:
    subject { "foo" }

    it { should eq "foo" }
  end

  context "when using an explicit subject" do
    subject { "foo" }

    it "should equal foo" do
      # BAD
      # although it's valid RSpec code and this test passes,
      # it's not okay to use `subject` here:
      expect(subject).to eq "foo"
    end
  end

  describe '.some_class_method' do
    it 'does something' do
      # ...
    end
  end

  describe '#some_instance_method' do
    it 'does something' do
      expect(something).to eq 'something'
    end
  end

  describe '#another_instance_method' do
    context 'when in one case' do
      it 'does something' do
        # ...
      end
    end

    context 'when in other case' do
      it 'does something else' do
        # ...
      end
    end
  end
end
```

## UNDECIDED Avoid let

```ruby
# BAD
describe ReportPolicy do
  let(:user) { User.new(report_ids: [1, 2]) }
  let(:report) { Report.new(id: 2) }

  describe "#allowed?" do
    context "when user has access to report" do
      it "returns true" do
        policy = ReportPolicy.new(user, report)

        expect(policy).to be_allowed
      end
    end

    context "when user does not have access to report" do
      it "returns false" do
        report.id = 3
        policy = ReportPolicy.new(user, report)

        expect(policy).not_to be_allowed
      end
    end
  end
end

# GOOD
describe ReportPolicy do
  describe "#allowed?" do
    context "when user has access to report" do
      it "returns true" do
        policy = build_policy(report_id: 2, allowed_report_ids: [1, 2])
        expect(policy).to be_allowed
      end
    end

    context "when user does not have access to report" do
      it "returns false" do
        policy = build_policy(report_id: 3, allowed_report_ids: [1, 2])
        expect(policy).not_to be_allowed
      end
    end
  end

  def build_policy(report_id:, allowed_report_ids:)
    user = instance_double("User", report_ids: allowed_report_ids)
    report = instance_double("Report", id: report_id)

    ReportPolicy.new(user, report)
  end
end

```

