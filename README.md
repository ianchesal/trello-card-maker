# trello-card-maker

[![Build Status](https://travis-ci.org/ianchesal/trello-card-maker.svg?branch=master)](https://travis-ci.org/ianchesal/trello-card-maker)

Makes a set of cards in a specific column on a Trello board. Stupid utility that let's me recreate a bunch of cards on a Trello board without having to do it by hand every time.

## Configuration

You need to configure your credentials for this to work. I've included `bin/auth-with-trello` to do this for you. It just:

* Fetches your developer key from https://trello.com/1/appKey/generate
* Uses that key to generate OAuth URL key from trello.com/1/authorize?key=TRELLO_DEVELOPER_PUBLIC_KEY&name=trello-card-maker&response_type=token&scope=read,write,account&expiration=never

It saves all of this information into `.config/auth.yml` for you.

It should look like this:

    ---
    :developer_public_key: TRELLO_DEVELOPER_PUBLIC_KEY
    :member_token: TRELLO_MEMBER_TOKEN

NEVER CHECK THIS INFORMATION IN! This is sensitive information and you don't want others to have it. The default repository `.gitignore` ignores this directory for a reason.

Configure the cards you want created in `.config/cards.yml`. This file has the form:

    ---
    :board:
      :name: BOARD_NAME
      :create: (true|false)
    :list:
      :name: LIST_NAME
      :create: (true|false)
      :card_prefix: OPTIONAL_PREFIX_FOR_EVERY_CARD
      :card_postfix: OPTIONAL_POSTFIX_FOR_EVERY_CARD
    :cards:
      - CARD_1
      - CARD_2
      - CARD_3

Once that's done run:

    bundle install

and you're ready to go! Prefix all the commands with `bundle exec <command>` when you're calling them.

## Usage

### `bundle exec bin/auth-with-trello`

Get credentials to use the tools with your Trello account.

### `bundle exec bin/make-cards`

Makes the cards for you on the Trello board. Reads the board, the list and the cards to create from the `.config/cards.yml` file.

Options:

* `--dry-run` -- Prints what it would have done, doesn't actually change the board

## Development

### Continuous Integration

I'm using Travis CI to build and test on every push to the public github repository. You can find the Travis CI page for this project here: https://travis-ci.org/ianchesal/xenforo-conversion/

### TODO Work

Please see [TODO.md](TODO.md) for the short list of big things I thought worth writing down.

## Contact Me

Questions or comments about `trello-card-maker`? Hit me up at ian.chesal@gmail.com.

