# chef_logstash cookbook

This is a Library Style cookbook that provides Resource Providers to create and
manage your [Logstash](http://logstash.net/) environment.

# Requirements

The following cookbooks are required to use this cookbook:

  + [runit](https://github.com/opscode-cookbooks/runit)
  + [java::openjdk](https://github.com/opscode-cookbooks/java)

# Usage

# Resources and Providers

## logstash_instance
The intention is to provide a stable interface to creating instances of
Logstash on your servers. This means creating a instance via
`logstash_instance` will download, install, and setup a functional
instance of Logstash but it does not handle any configuration details.

The following actions are supported and `:create` is the default:

 + `:create` - Creates a named instance of Logstash. This action will
download logstash `:version` to the `:dst_dir`. It creates the `:user`
and `:group` used to run Logstash. And finally it creates the `runit`
resource required to manage the service. It does not _start_ the service
as that is a job for `:enable`.

 + `:enable`
 + `:destroy`
 + `:nothing`

These attributes are defined in the resource:

 + `:name`
 + `:user`
 + `:group`
 + `:conf_dir`
 + `:dst_dir`
 + `:version`
 + `:url`
 + `:checksum`
 + `:nofiles`

Usage example:
```ruby
  logstash_instance 'test' do
    url node.logstash.url
    checksum node.logstash.checksum
  end
```

## logstash_config

# Contributing

## Testing

[![Build Status](https://travis-ci.org/miah/chef_logstash.png)](https://travis-ci.org/miah/chef_logstash)

## Code Style

This code follows the [Ruby Style Guide](https://github.com/miah/ruby-style-guide) and all contributions should as well.

The code style is checked by [tailor](https://github.com/turboladen/tailor) and can be checked by executing `rake test:tailor` or `tailor`. This is automatically checked by [Travis-CI](https://travis-ci.org/miah/chef_logstash).

# Author

Author:: Miah Johnson (<miah@chia-pet.org>)

# License
```
   Copyright 2013 Miah Johnson

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```
