# Windows Security Policy Helper Cookbook

Provides a helper security policy resource, and template with attributes for managing your Windows local security and security databases.

## Requirements

### Platforms

- Windows Server 2012 (R1, R2)

### Chef

- Chef 12.1+

## Resources

### security_policy

#### Actions

- `:configure` - Applies configuration from a template to an existing SDB.
- `:export` - Exports SDB settings to the local filesystem.
- `:import` - Imports from a template into an SDB- can create a new SDB in the process.

#### Properties

- `template` - Path to the teamplate on the filesystem.
- `database` - The security database (*.sdb) you wish to affect.
- `log_location` - Location to write logs to.

#### Examples

Configure an existing security database.

```ruby
security_policy 'Local Policy' do
    template 'C:\Windows\security\templates\chefNewPolicy.inf'
    database 'C:\Windows\security\database\chef.sdb'
    action :configure
end
```

## Recipes

The following recipes are available in this cookbook.

### default
Unused.

### template
This recipe is used to create a template that can be used to configure a security database. All of the accepted settings are attributes in this cookbook.



## Usage

Place an explicit dependency on this cookbook (using depends in the cookbook's metadata.rb) from any cookbook where you would like to use the Windows-specific resources/providers that ship with this cookbook.

```ruby
depends 'windows'
```

## License & Authors

- Author:: Joe Gardiner ([joe@chef.io](mailto:joe@chef.io))

```text
Copyright 2011-2017, Chef Software, Inc.

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