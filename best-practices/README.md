Best Practices
==============

A guide for programming well.

General
-------

* These are not to be blindly followed; strive to understand these and ask
  when in doubt.
* Don't duplicate the functionality of a built-in library.
* Don't swallow exceptions or "fail silently."
* Don't write code that guesses at future functionality.
* [Exceptions should be exceptional].
* [Keep the code simple].

[Exceptions should be exceptional]: http://www.readability.com/~/yichhgvu
[Keep the code simple]: http://www.readability.com/~/ko2aqda2

Object-Oriented Design
----------------------

* Avoid global variables.
* Avoid long parameter lists.
* Limit collaborators of an object (entities an object depends on).
* Limit an object's dependencies (entities that depend on an object).
* Prefer composition over inheritance.
* Prefer small methods. Between one and five lines is best.
* Prefer small classes with a single, well-defined responsibility. When a
  class exceeds 100 lines, it may be doing too many things.
* [Tell, don't ask].

[Tell, don't ask]: http://robots.thoughtbot.com/post/27572137956/tell-dont-ask

Ruby
----

* Avoid optional parameters. Does the method do too much?
* Avoid monkey-patching.
* Prefer classes to modules when designing functionality that is shared by
  multiple models.

Rails
-----

* [Add foreign key constraints][fkey] in migrations.
* Avoid bypassing validations with methods like `save(validate: false)`,
  `update_attribute`, and `toggle`.
* Avoid instantiating more than one object in controllers.
* Avoid naming methods after database columns in the same class.
* Don't change a migration after it has been merged into master if the desired
  change can be solved with another migration.
* Don't reference a model class directly from a view.
* Don't return false from `ActiveModel` callbacks, but instead raise an
  exception.
* Don't use instance variables in partials. Pass local variables to partials
  from view templates.
* Don't use SQL or SQL fragments (`where('inviter_id IS NOT NULL')`) outside of
  models.
* Generate necessary [Spring binstubs] for the project, such as `rake` and
  `rspec`, and add them to version control.
* If there are default values, set them in migrations.
* Keep `db/schema.rb` or `db/development_structure.sql` under version control.
* Use only one instance variable in each view.
* Use SQL, not `ActiveRecord` models, in migrations.
* Use the [`.ruby-version`] file convention to specify the Ruby version and
  patch level for a project.
* Use `_url` suffixes for named routes in mailer views and [redirects].  Use
  `_path` suffixes for named routes everywhere else.
* Validate the associated `belongs_to` object (`user`), not the database column
  (`user_id`).
* Use `db/seeds.rb` for data that is required in all environments.
* Use `dev:prime` rake task for development environment seed data.
* Prefer `cookies.signed` over `cookies` to [prevent tampering].
* Prefer `Time.current` over `Time.now`
* Prefer `Date.current` over `Date.today`
* Prefer `Time.zone.parse("2014-07-04 16:05:37")` over `Time.parse("2014-07-04 16:05:37")`
* Use `ENV.fetch` for environment variables instead of `ENV[]`so that unset
  environment variables are detected on deploy.

[fkey]: http://robots.thoughtbot.com/referential-integrity-with-foreign-keys
[`.ruby-version`]: https://gist.github.com/fnichol/1912050
[redirects]: http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.30
[Spring binstubs]: https://github.com/sstephenson/rbenv/wiki/Understanding-binstubs
[prevent tampering]: http://blog.bigbinary.com/2013/03/19/cookies-on-rails.html

Testing
-------

* Avoid `any_instance` in rspec-mocks and mocha. Prefer [dependency injection].
* Avoid using `subject` explicitly *inside of an* RSpec `it` block.
  [Example][subject-example].
* Avoid using instance variables in tests.
* Disable real HTTP requests to external services with
  `WebMock.disable_net_connect!`.
* Don't test private methods.
* Use [stubs and spies] \(not mocks\) in isolated tests.
* Use a single level of abstraction within scenarios.
* Use an `it` example or test method for each execution path through the method.
* Use [assertions about state] for incoming messages.
* Use stubs and spies to assert you sent outgoing messages.
* Use a [Fake] to stub requests to external services.
* Use integration tests to execute the entire app.

[dependency injection]: http://en.wikipedia.org/wiki/Dependency_injection
[subject-example]: ../style/testing/unit_test_spec.rb
[`Delayed::Job` matcher]: https://gist.github.com/3186463
[stubs and spies]: http://robots.thoughtbot.com/post/159805295/spy-vs-spy
[assertions about state]: https://speakerdeck.com/skmetz/magic-tricks-of-testing-railsconf?slide=51
[Fake]: http://robots.thoughtbot.com/post/219216005/fake-it


Browsers
--------

* Don't support IE6 or IE7.


Angular
-------

* [Avoid manual dependency annotations][annotations]. Disable mangling or use a
  [pre-processor][ngannotate] for annotations.
* Prefer `factory` to `service`. If you desire a singleton, wrap the singleton
  class in a factory function and return a new instance of that class from the
  factory.
* Prefer the `translate` directive to the `translate` filter for [performance
  reasons][angular-translate].
* Don't use the `jQuery` or `$` global. Access jQuery via `angular.element`.

[annotations]: http://robots.thoughtbot.com/avoid-angularjs-dependency-annotation-with-rails
[ngannotate]: https://github.com/kikonen/ngannotate-rails
[angular-translate]: https://github.com/angular-translate/angular-translate/wiki/Getting-Started#using-translate-directive
