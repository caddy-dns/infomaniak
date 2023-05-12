infomaniak module for Caddy
===========================

This package contains a DNS provider module for [Caddy](https://github.com/caddyserver/caddy). It can be used to manage DNS records with [infomaniak](https://infomaniak.com).

## Caddy module name

```
dns.providers.infomaniak
```

## Config examples

To use this module for the ACME DNS challenge, [configure the ACME issuer in your Caddy JSON](https://caddyserver.com/docs/json/apps/tls/automation/policies/issuer/acme/) like so:

```json
{
	"module": "acme",
	"challenges": {
		"dns": {
			"provider": {
				"name": "infomaniak",
				"api_token": "{env.INFOMANIAK_API_TOKEN}"
			}
		}
	}
}
```

or with the Caddyfile:

```
# globally
{
	acme_dns infomaniak {env.INFOMANIAK_API_TOKEN}
}
```

```
# one site
tls {
	dns infomaniak {env.INFOMANIAK_API_TOKEN}
}
```

You can replace `{env.INFOMANIAK_API_TOKEN}` with the actual auth token if you prefer to put it directly in your config instead of an environment variable.

## Authenticating

Refer to [the README of the libdns package](https://github.com/libdns/infomaniak) for information on how to get your infomaniak API token.