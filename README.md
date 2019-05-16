# rubocop-config

Teachable's Rubocop configuration, it's in a public repository so we can easily inherit from these settings.

By default, we enable all the cops and only disable the ones we don't like.

* [Rubocop Documentation](https://docs.rubocop.org/en/stable/)
* [Configuration Options](https://github.com/bbatsov/rubocop/blob/master/config/default.yml)
* [Enabled by default](https://github.com/bbatsov/rubocop/blob/master/config/enabled.yml)
* [Disabled by default](https://github.com/bbatsov/rubocop/blob/master/config/disabled.yml)
* [Rubocop Sourcecode](https://github.com/rubocop-hq/rubocop)

### Usage

You inherit from the configurations you need and you can override settings in your own `.rubocop.yml` file.

Here's a common place to start for a Rails project:

``` yaml
require: rubocop-performance

inherit_from:
  - https://raw.githubusercontent.com/UseFedora/rubocop-config/master/config/ruby.yml
  - https://raw.githubusercontent.com/UseFedora/rubocop-config/master/config/performance.yml
  - https://raw.githubusercontent.com/UseFedora/rubocop-config/master/config/rails.yml

AllCops:
  EnabledByDefault: true
  ExtraDetails: true
  DisplayCopNames: true
  DisplayStyleGuide: true
  TargetRubyVersion: 2.6
  TargetRailsVersion: 5.2
```

The reason `performance.yml` is separate is because you need a separate gem for it. Add the `rubocop-performance` gem to your Gemfile to get it.

Also add this to your `.gitignore` file to not commit the cached files.

```
.rubocop-*
```

### Testing

To test the config, just run `rubocop`.
