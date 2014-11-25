# Suid3 with Ansible and Vagrant

## Prerequisites

You need to have installed the following components:

- [Ruby](https://www.ruby-lang.org/en/installation/)
- [Vagrant](https://www.vagrantup.com/downloads.html)
- [Ansible](http://docs.ansible.com/intro_installation.html)

## Bootstraping

To create virtual machines run in project directory:

    vagrant up

The command above will download ubuntu and build three virtual machines with `squid3` installed and running.

## Usage

Virtual machine's parameters are as follows:

|             | squid                           |
|-------------|---------------------------------|
| mac address | `080000000101`                  |
| eth1 config | `192.168.56.101` `080000000102` |

You can ssh into machine as:

    vagrant ssh

You can use machine as a proxy:

    curl -x 192.168.56.101:3128 http://www.example.com/

## Authentication

Squid3 uses HTTP basic authentication with the following credentials predefined:

|   | **login** | **password** |
|---|-----------|--------------|
| 1 | admin     | admin        |
| 2 | user      | password     |

You can modify this values in [`credentials.yml`](https://github.com/KamilLelonek/squid3-permission-proxies/blob/master/vars/credentials.yml)

To authenticate via proxy use `curl` as follows:

    curl --proxy-user user:password -x 192.168.56.101:3128 http://example.com/

## Aliases

You can use some useful commands to manage `squid3`:

- `showcache`
- `clearcache`
- `showlogs`
- `clearlogs`

## Help

If anything goes wrong you can destroy previously created machines by:

    vagrant destroy

That won't delete downloaded Ubuntu image. Another useful commands are:

- `vagrant provision` - setup machines once again
- `vagrant reload` - restart machines and apply new configuration

## Resources:

- http://tecadmin.net/configure-squid-proxy-server-mac-address-based-filtering/
- http://www.deckle.co.uk/squid-users-guide/squid-access-control-and-access-control-operators.html
- http://wiki.squid-cache.org/SquidFaq/SquidAcl


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/KamilLelonek/squid3-permission-proxies/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

