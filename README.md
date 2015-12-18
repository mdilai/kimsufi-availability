## Kimsufi availability

Kimsufi servers are very interesting but extremely difficult to obtain. This script parses the OVH API and sends you a mail and/or SMS when a server is available.
Based on https://github.com/ncrocfer/kimsufi-availability
Detailed usage guide at https://quotehex.com/how-to-guaranteed-quickly-get-kimsufi-server/

## Usage

    Usage:
      kimsufi.py [options]
      kimsufi.py <model>... [options]

    Options:
      -h, --help     Show this help.
      -v, --version  Show version.
      -m, --mail     Send a mail when a server is available.
      -s, --sms      Send an SMS when a server is avaliable.

    Examples:
      kimsufi.py
      kimsufi.py KS-1 KS-3
      kimsufi.py KS-1 --mail
      kimsufi.py KS-2 --sms --mail


## Output example

    $ python kimsufi.py KS-1

    KS-1
    ====
    Gravelines : 1H-high

    =======
    RESULT : 1 server is available on Kimsufi
    =======

    Order KS-1 - https://www.kimsufi.com/en/order/kimsufi.cgi?hard=150sk10

## Installation

The script works on Python 2.x and 3.x. It's just a simple script, so no _setup.py_ is offer :

    $ git clone https://github.com/mdilay/kimsufi-availability.git
    $ cd kimsufi-availability
    $ pip install -r requirements.txt
    $ python kimsufi.py

## Configuration

A mail can be sent with the `--mail` option. You can configure it with a `config.json` file : 

    $ cp config.json.sample config.json
    $ vim config.json
    {
        "email": {
                "host": "...",
                "port": 587,
                "username": "...",
                "password": "...",
                "mail_from": "...",
                "mail_to": "..."
        }
    }

An SMS can be sent with the `--sms` option. You can configure it with a `config.json` file :

    $ vim config.json
    {
	"sms": {
                "account_sid": "",
                "auth_token": "",
                "sms_to": "",
                "sms_from": ""
        }
    }

SMS are sent via free Twilio account (https://www.twilio.com). Just register, get API data and put in your config.json.

## Using autocheck script

You can use built-in script kimsufi.sh to autocheck OVH avaliability every 8 seconds (maximum delay allowed by OVH API) and get SMS/mail with order link as soon as possibly. Just modify the script for needed model and message type (sms, mail or both). How to run:

    nohup ./kimsufi.sh &

## License

This script is under the [Beerware](http://en.wikipedia.org/wiki/Beerware) license.
