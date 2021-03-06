# Zuora [![Build Status](https://secure.travis-ci.org/wildfireapp/zuora.png?branch=master)](http://travis-ci.org/wildfireapp/zuora) [![Gemnasium](https://gemnasium.com/wildfireapp/zuora.png)](https://gemnasium.com/wildfireapp/zuora)

This library allows you to interact with [Zuora](http://www.zuora.com) billing platform directly using 
familiar [ActiveModel](https://github.com/rails/rails/tree/master/activemodel) based objects.

## Requirements
  * [bundler](https://github.com/carlhuda/bundler)
  * [active_support](https://github.com/rails/rails/tree/master/activesupport)
  * [savon](https://github.com/rubiii/savon)
  * [wasabi](https://github.com/rubiii/wasabi)

All additional requirements for development should be referenced in the provided zuora.gemspec and Gemfile.

## Installation

    git clone git@github.com:Josephu/zuora.git

## Getting Started

    $ bundle install
    $ bundle exec irb -rzuora

    Zuora.configure(:username => 'USER', :password => 'PASS')

    account = Zuora::Objects::Account.create(:account_number => '12345')
    # => <Zuora::Objects::Account :account_number => 12345, :id => 'abc123'>
    Zuora::Objects::Account.find('abc123')
    # => <Zuora::Objects::Account :account_number => 12345, :id => 'abc123'>
    account.destroy
    # => true

## Added Methods

    # Use find by to query with specific column
    Zuora::Objects::Account.find_by(:account_number => '12345')
    # => <Zuora::Objects::Account :account_number => 12345, :id => 'abc123'>

    # Only query a column, eg. "account_number"
    Zuora::Objects::Account.where(:account_number => '12345', "account_number") 
    # => [<Zuora::Objects::Account :account_number => 12345, :id => 'abc123'>]

    # Query 2 columns
    Zuora::Objects::Account.where(:account_number => '12345', "account_number, name") 
    # => [<Zuora::Objects::Account :account_number => 12345, :name => "test", :id => 'abc123'>]

## Added Module Support

  * Credit balance adjustment
  * Payment
  * Invoice payment
  * Subscription request => support price change
  * Amendment => support cancellation

## Documentation
  You can generate up to date documentation with the provided a rake task.

    $ rake doc
    $ open doc/index.html

## Advanced Usage
  Review the generated documentation for usage patterns and examples of using specific zObjects.

## Test Suite
  This library comes with a full test suite, which can be run using the stanard rake utility.

      $ rake spec

## Live Integration Suite
  There is also a live suite which you can test against your sandbox account.
  This can by ran by setting up your credentials and running the integration suite.

  **Do not run this suite using your production credentials. Doing so may destroy
  data although every precaution has been made to avoid any destructive behavior.**

      $ ZUORA_USER=login ZUORA_PASS=password rake spec:integrations

## Support & Maintenance
  This library currently supports Zuora's SOAP API version 38.

## Contributors
  * Josh Martin <josh.martin@wildfireapp.com>
  * Alex Reyes <alex.reyes@wildfireapp.com>
  * Wael Nasreddine <wael.nasreddine@wildfireapp.com>

## Credits
  * [Wildfire Ineractive](http://www.wildfireapp.com) for facilitating the development and maintenance of the project.
  * [Zuora](http://www.zuora.com) for providing us with the opportunity to share this library with the community.

