# Contentful Bootstrap

A small CLI tool for getting started with Contentful

## Contentful
[Contentful](http://www.contentful.com) is a content management platform for web applications,
mobile apps and connected devices. It allows you to create, edit & manage content in the cloud
and publish it anywhere via powerful API. Contentful offers tools for managing editorial
teams and enabling cooperation between organizations.

## What does `contentful_bootstrap` do?
The aim of `contentful_bootstrap` is to have developers setting up their Contentful environment
in a single command

## How to Use

### Installation

```bash
$ gem install contentful_bootstrap
```

### First Usage

```bash
$ contentful_bootstrap init <space_name> [--template template_name] [--config CONFIG_PATH]
```


Then you can create other spaces by doing:

```bash
$ contentful_bootstrap create_space <space_name> [--template template_name] [--config CONFIG_PATH]
```


You can also generate new Delivery API Tokens by doing:

```bash
$ contentful_bootstrap generate_token <space_id> [--name token_name] [--config CONFIG_PATH]
```

### Available templates

The available templates for your spaces are:

```
blog
gallery
catalogue
```

This will get you started with Contentful by setting up a Space with some Demo Data to get you
started as soon as possible with development using our API.

### Using from within other applications

Include `contentful_bootstrap` to your project's `Gemfile`

```ruby
gem "contentful_bootstrap"
```

Require `contentful_bootstrap`

```ruby
require 'contentful/bootstrap'
```

To do the complete `init` process

```ruby
Contentful::Bootstrap::Commands.new.init("space_name", "template_name") # Template Name is optional
```


To create a new Space or Token

```ruby
# Create a new Space
Contentful::Bootstrap::Commands.new.create_space("space_name", "template_name") # Template Name is optional

# Create a new CDA Access Token
Contentful::Bootstrap::Commands.new.generate_token("space_id", "token_name") # Token Name is optional
```

Optionally, `Commands#new` will take a parameter for specifying a configuration path

### Configuration

Contentful Bootstrap will read by default from `~/.contentfulrc`, but you can provide your own
file by using the `--config CONFIG_PATH` parameter

If you don't have `~/.contentfulrc` created, you will be prompted if you want to create it

#### Configuration Format

The configuration file will be in `ini` format and looks like the following

```ini
[global]
CONTENTFUL_MANAGEMENT_ACCESS_TOKEN = a_management_access_token
CONTENTFUL_DELIVERY_ACCESS_TOKEN = a_delivery_acces_token      ; Delivery Access Token is not required for this tool, but can be generated by it
```

## Contributing

Feel free to improve this tool by submitting a Pull Request. For more information,
please check [CONTRIBUTING.md](./CONTRIBUTING.md)
