# Yourls

[YOURLS](http://yourls.org) is an open-source, PHP url-shortening service.

## Installation

    gem install yourls

## Usage

Create a Yourls client using your hostname and api key as follows:

    yourls = Yourls.new(your_hosted_yourls_address, your_hosted_yourls_api_key)

You can then interact with the client to shorten or expand urls or to get statistics about your service:

    yourls.shorten('http://www.google.com')
    yourls.shorten('http://www.google.com', :keyword => 'goog') # Creates a custom keyword url
    yourls.expand('goog')
    yourls.stats

`expand` and `shorten` both will return a `Yourls::Url` object

    url = yourls.shorten('http://www.google.com', :keyword => 'goog')
    url.short_url #=> "http://your-service/goog"
    url.long_url #=> "http://www.google.com"
    url.keyword #=> "goog"

## About this fork

	add delete method for yourls gem.

	update yourls-api.php, insert below code to yourls-api.php:

	// Delete a short link by keyword
    case 'delete':
        $keyword = ( isset( $_REQUEST['keyword'] ) ? $_REQUEST['keyword'] : '' );
        $query = yourls_delete_link_by_keyword( $_REQUEST['keyword'] );
        $return = array(
            'keyword'  => $keyword,
            'simple'   => $query,
            'message'  => $query,
            'statusCode' => 200,
        );
        break;

	this fork extend delete for yourls gem:

	yourls.delete('goog')



## Copyright

Copyright (c) 2010 [Three Stage Media, Inc.](http://www.threestage.com) and licensed under the MIT License (see MIT-LICENSE for details).
