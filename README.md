# ronin-vulns

[![CI](https://github.com/ronin-rb/ronin-vulns/actions/workflows/ruby.yml/badge.svg)](https://github.com/ronin-rb/ronin-vulns/actions/workflows/ruby.yml)
[![Code Climate](https://codeclimate.com/github/ronin-rb/ronin-vulns.svg)](https://codeclimate.com/github/ronin-rb/ronin-vulns)

* [Website](https://ronin-rb.dev/)
* [Source](https://github.com/ronin-rb/ronin-vulns)
* [Issues](https://github.com/ronin-rb/ronin-vulns/issues)
* [Documentation](https://ronin-rb.dev/docs/ronin-vulns/frames)
* [Slack](https://ronin-rb.slack.com) |
  [Discord](https://discord.gg/6WAb3PsVX9) |
  [Twitter](https://twitter.com/ronin_rb)

## Description

ronin-vulns is a Ruby library for blind vulnerability testing. It currently
supports testing for Local File Inclusion (LFI), Remote File Inclusion (RFI),
SQL injection (SQLi), and reflective Cross Site Scripting (XSS).

## Features

* Supports testing for:
  * Local File Inclusion (LFI)
  * Remote File Inclusion (RFI)
  * SQL Injection (SQLi)
  * reflected Cross Site Scripting (XSS)
* Supports testing:
  * URL query parameters.
  * HTTP Headers.
  * HTTP `Cookie` parameters.
  * Form parameters.

## Examples

### Remote File Inclusion (RFI)

Test a URL for Remote File Inclusion (RFI):

```ruby
require 'ronin/vulns/rfi'

vuln = Ronin::Vuln::RFI.test('http://www.example.com/page.php?lang=en')
# => #<Ronin::Vuln::RFI: ...>
```

Finds all Remote File Inclusion (RFI) vulnerabilities for a given URL:

```ruby
vulns = Ronin::Vuln::RFI.scan('http://www.example.com/page.php?lang=en')
# => [#<Ronin::Vuln::RFI: ...>, ...]

vulns = Ronin::Vuln::RFI.scan('http://www.example.com/page.php?lang=en') do |vuln|
  puts "Found RFI on #{vuln.url} query param #{vuln.query_param}"
end
# => [#<Ronin::Vuln::RFI: ...>, ...]
```

### Local File Inclusion (LFI)

Test a URL for Remote File Inclusion (RFI):

```ruby
require 'ronin/vulns/rfi'

vuln = Ronin::Vuln::RFI.test('http://www.example.com/page.php?lang=en')
# => #<Ronin::Vuln::RFI: ...>
```

Finds all Remote File Inclusion (RFI) vulnerabilities for a given URL:

```ruby
vulns = Ronin::Vuln::RFI.scan('http://www.example.com/page.php?lang=en')
# => [#<Ronin::Vuln::RFI: ...>, ...]

vulns = Ronin::Vuln::RFI.scan('http://www.example.com/page.php?lang=en') do |vuln|
  puts "Found RFI on #{vuln.url} query param #{vuln.query_param}"
end
```

### Server Side Template Injection (SSTI)

Test a URL for Server Side Template Injection (SSTI):

```ruby
require 'ronin/vulns/rfi'

vuln = Ronin::Vuln::SSTI.test('http://www.example.com/page.php?lang=en')
# => #<Ronin::Vuln::SSTI: ...>
```

Finds all Server Side Template Injection (SSTI) vulnerabilities for a given URL:

```ruby
vulns = Ronin::Vuln::SSTI.scan('http://www.example.com/page.php?lang=en')
# => [#<Ronin::Vuln::SSTI: ...>, ...]

vulns = Ronin::Vuln::SSTI.scan('http://www.example.com/page.php?lang=en') do |vuln|
  puts "Found SSTI on #{vuln.url} query param #{vuln.query_param}"
end
# => [#<Ronin::Vuln::SSTI: ...>, ...]
```

## Requirements

* [Ruby] >= 3.0.0
* [ronin-support] ~> 1.0

## Install

```shell
$ gem install ronin-vulns
```

### Gemfile

```ruby
gem 'ronin-vulns', '~> 0.1'
```

### gemspec

```ruby
gem.add_dependency 'ronin-vulns', '~> 0.1'
```

## Development

1. [Fork It!](https://github.com/ronin-rb/ronin-vulns/fork)
2. Clone It!
3. `cd ronin-vulns/`
4. `bundle install`
5. `git checkout -b my_feature`
6. Code It!
7. `bundle exec rake spec`
8. `git push origin my_feature`

## License

Copyright (c) 2022 Hal Brodigan (postmodern.mod3 at gmail.com)

ronin-vulns is free software: you can redistribute it and/or modify
it under the terms of the GNU Lesser General Public License as published
by the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

ronin-vulns is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public License
along with ronin-vulns.  If not, see <https://www.gnu.org/licenses/>.

[Ruby]: https://www.ruby-lang.org
[ronin-support]: https://github.com/ronin-rb/ronin-support#readme
