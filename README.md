# rubocop-config

Teachable's Rubocop configuration, it's in a public repository so we can easily
inherit from these settings.

By default, we enable all the cops and only disable the ones we don't like.

* [Rubocop Documentation](https://docs.rubocop.org/en/stable/)
* [Configuration Options](https://github.com/bbatsov/rubocop/blob/master/config/default.yml)
* [Enabled by default](https://github.com/bbatsov/rubocop/blob/master/config/enabled.yml)
* [Disabled by default](https://github.com/bbatsov/rubocop/blob/master/config/disabled.yml)
* [Rubocop Sourcecode](https://github.com/rubocop-hq/rubocop)

## Usage

### `.rubocop.yml`

You inherit from the configurations you need and you can override settings in
your own `.rubocop.yml` file.

Here's a common place to start for a Rails project:

``` yaml
require:
  - rubocop-performance
  - rubocop-rails
  - rubocop-rspec

inherit_from:
  - https://config.teachablecdn.com/rubocop/ruby.yml
  - https://config.teachablecdn.com/rubocop/performance.yml
  - https://config.teachablecdn.com/rubocop/rails.yml
  - https://config.teachablecdn.com/rubocop/rspec.yml

AllCops:
  EnabledByDefault: true
  ExtraDetails: true
  DisplayCopNames: true
  DisplayStyleGuide: true
  TargetRubyVersion: 2.6
  TargetRailsVersion: 5.2
```

And for non-rails projects:

``` yaml
require:
  - rubocop-performance
  - rubocop-rspec

inherit_from:
  - https://config.teachablecdn.com/rubocop/ruby.yml
  - https://config.teachablecdn.com/rubocop/performance.yml
  - https://config.teachablecdn.com/rubocop/rspec.yml

AllCops:
  EnabledByDefault: true
  ExtraDetails: true
  DisplayCopNames: true
  DisplayStyleGuide: true
  TargetRubyVersion: 2.6
```

### `Gemfile`

The reason `performance.yml` is separate is because you need a separate gem for
it. Add the `rubocop-performance` gem to your `Gemfile` to get it.

``` ruby
group :development, :test do
  gem "rubocop-performance", require: false
  gem "rubocop-rails",       require: false
  gem "rubocop-rspec",       require: false
end
```

We don't want to require it in normal use, just when running the rubocop command.

And it should go without saying that `rubocop-rails` should only be added when
you are in a Rails project. The same goes for `rubocop-rspec`.

### `.gitignore`

Also add this to your `.gitignore` file to not commit the cached configuration files.

```
.rubocop-*
```


### Testing

To test the config, just run `bundle exec rubocop`.
