Statistic Information
#####################

All calls to **/stats/** endpoint only work with a beta API account.

TLDs Statistic
**************

Command
=======

**GET /stats/tlds**

Arguments
    :limit: limit result to X tlds - default 30
    :details: if true, result contains details

Response
    :tlds: list of TLD objects sort by domain_count descendering
    :stats: total stats object

Total Stats Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds
    
TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :registry: Registry object
    :backend: Backend object
    :current_stage: name of current stage
    :total_domains: total count of registered domains in this TLD
    :registrars: list of Registrars objects (only on detailed listing)
    :total_registrars: total count of registrars (only on detailed listing)
    
Registry Object
    :id: id of Registry
    :name: name of Registry
    :url: url of Registry

Backend Object
    :id: id of Backend
    :name: name of Backend
    :url: url of Backend

Registrar Object
    :id: id of Registrar
    :iana_id: registrar IANA id
    :name: name of Registrar
    :url: homepage of Registrar
    :registrar_group: Registrar Group object
    :domain_count: total registered domains

Registrar Group Object
    :name: name of Registrar Group
    :url: homepage of Registrar Group
    
Example
=======

Request

::

    GET /stats/tlds

Response

::

    {
        "resData": {
            "tlds": { 
                "xyz": {
                    "zone": "xyz",
                    "zone_utf8": "xyz",
                    "registry": {
                        "name": "XYZ.COM LLC",
                        "id": "XYZCOM-LLC",
                        "info_url": "http:\/\/ntldstats.com\/registry\/XYZCOM-LLC",
                        "url": "http:\/\/nic.xyz"
                    },
                    "backend": {
                        "name": "CentralNic",
                        "id": "CentralNic",
                        "info_url": "http:\/\/ntldstats.com\/backend\/CentralNic",
                        "url": "http:\/\/www.centralnic.com"
                    },
                    "current_stage": "GA",
                    "total_domains": 704262
                }
            },
            "stats": {
                "total_domains": 3097027,
                "total_tlds": 430
            }   
        },
        "code": 1000,
        "msg":"Command completed successfully",
    }

Sample Link: https://beta.api.ntldstats.net/stats/tlds

TLD Statistic
*************

Command
=======

**GET /stats/tld/<zone>**

Arguments
    :limit: limit result of registrars

Response
    :tld: TLD Object
    :stats: total stats object

Total Stats Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds
    
TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :registry: Registry object
    :backend: Backend object
    :current_stage: name of current stage
    :total_domains: total count of registered domains in this TLD
    :total_registrars: total count of registrars
    :registrars: list of Registrars objects
    
Registry Object
    :id: id of Registry
    :name: name of Registry
    :info_url: public nTLDStats_ URL to get more information about Registry
    :url: url of Registry

Backend Object
    :id: id of Backend
    :name: name of Backend
    :info_url: public nTLDStats_ URL to get more information about Backend
    :url: url of Backend
 
Registrar Object
    :id: id of Registrar
    :iana_id: registrar IANA id
    :name: name of Registrar
    :url: homepage of Registrar
    :registrar_group: Registrar Group object
    :domain_count: total registered domains

Registrar Group Object
    :name: name of Registrar Group
    :url: homepage of Registrar Group

Example
=======

Request

::

    GET /stats/tld/berlin

Response

::

    {
        "resData": {
            "tld": {
                "zone": "berlin",
                "zone_utf8": "berlin",
                "registry": {
                    "id": "dotBERLIN-GmbH-Co-KG",
                    "name": "dotBERLIN GmbH & Co. KG",
                    "url": "http:\/\/nic.berlin"
                },
                "backend": {
                    "id": "TLDBOX-Registrydienstleistungen-GmbH",
                    "name": "TLD-BOX Registrydienstleistungen GmbH",
                    "url": "http:\/\/www.tld-box.at"
                },
                "total_domains": 153742,
                "total_registrars": 45,
                "registrars": [{
                    "iana_id": "151",
                    "name": "PSI-USA, Inc. dba Domain Robot",
                    "url": "http:\/\/www.psi-usa.info",
                    "registrar_group": {
                        "name": "InterNetX GmbH",
                        "url": null
                    },
                    "domain_count": 92056
                }],
                "current_stage": "GA"
            },
            "stats": {
                "total_domains": 3111803,
                "total_tlds": 431
            }
        },
        "code": 1000,
        "msg": "Command completed successfully"
    }

Sample Link: https://beta.api.ntldstats.net/stats/tld/berlin

Registrars Statistic
********************

Command
=======

**GET /stats/registrars**

Arguments
    :limit: limit result to X tlds - default 30
    :details: if true, result contains details

Response
    :registrars: list of Registrar Objects
    :stats: total stats object

Total Stats Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds
    
Registrar Object
    :id: id of Registrar
    :iana_id: registrar IANA id
    :name: name of Registrar
    :url: homepage of Registrar
    :registrar_group: Registrar Group object
    :total_domains: total registered domains
    :tlds: list of TLD objects (only on detailed listing)
    :total_tlds: total count of TLDs (only on detailed listing)
    
Registrar Group Object
    :name: name of Registrar Group
    :url: homepage of Registrar Group

TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :current_stage: name of current stage
    :domain_count: total count of registered domains in this TLD
    
Example
=======

Request

::

    GET /stats/registrars

Response

::

    {
        "resData": {
            "stats": {
                "total_domains": 3111803,
                "total_tlds": 431
            },
            "registrars": [{
                "id": "146",
                "iana_id": "146",
                "name": "GoDaddy.com, LLC",
                "url": "http:\/\/www.godaddy.com",
                "registrar_group": {
                    "name": "GoDaddy Group",
                    "url": "http:\/\/godaddy.com\/"
                },
                "total_domains": 490765
            }]
        },
        "code": 1000,
        "msg": "Command completed successfully"
    }

Sample Link: https://beta.api.ntldstats.net/stats/registrars

Registrar Statistic
*******************

Command
=======

**GET /stats/registrar/<iana_id>**

Arguments
    :limit: limit result of tlds

Response
    :registrar: Registrar Object
    :stats: total stats object

Total Stats Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds
    
Registrar Object
    :id: id of Registrar
    :iana_id: registrar IANA id
    :name: name of Registrar
    :url: homepage of Registrar
    :registrar_group: Registrar Group object
    :total_domains: total registered domains
    :total_tlds: total count of TLDs
    :tlds: list of TLD objects
    
Registrar Group Object
    :name: name of Registrar Group
    :url: homepage of Registrar Group

TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :current_stage: name of current stage
    :domain_count: total count of registered domains in this TLD

Example
=======

Request

::

    GET /stats/registrar/146

Response

::

    {
        "resData": {
            "registrar": {
                "id": "146",
                "iana_id": "146",
                "name": "GoDaddy.com, LLC",
                "url": "http:\/\/www.godaddy.com",
                "registrar_group": {
                    "name": "GoDaddy Group",
                    "url": "http:\/\/godaddy.com\/"
                },
                "total_domains": 490765,
                "total_tlds": 220,
                "tlds": [{
                    "zone": "guru",
                    "zone_utf8": "guru",
                    "domain_count": 44201,
                    "current_stage": "GA"
                }]
            },
            "stats": {
                "total_domains": 3111803,
                "total_tlds": 431
            }
        },
        "code": 1000,
        "msg": "Command completed successfully"
    }

Sample Link: https://beta.api.ntldstats.net/stats/registrar/146

Backends Statistic
******************

Command
=======

**GET /stats/backends**

Arguments
    :limit: limit result to X tlds - default 30
    :details: if true, result contains details

Response
    :backends: list of Backend Objects
    :stats: total stats object

Total Stats Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds

Backend Object
    :id: id of Backend
    :name: name of Backend
    :url: homepage of Backend
    :total_domains: total registered domains
    :tlds: list of TLD objects (only on detailed listing)
    :total_tlds: total count of TLDs (only on detailed listing)
    
TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :current_stage: name of current stage
    :domain_count: total count of registered domains in this TLD
    
Example
=======

Request

::

    GET /stats/backends

Response

::

    {
        "resData": {
            "stats": {
                "total_domains": 3111803,
                "total_tlds": 431
            },
            "backends": [{
                "id": "Donuts-Inc",
                "name": "Donuts Inc.",
                "url": "http:\/\/www.donuts.co",
                "total_domains": 1050611
            }]
        },
        "code": 1000,
        "msg": "Command completed successfully"
    }

Sample Link: https://beta.api.ntldstats.net/stats/backends

Backend Statistic
*****************

Command
=======

**GET /stats/backend/<id>**

Arguments
    :limit: limit result of tlds

Response
    :backend: Backend Object
    :stats: total stats object

Total Stats Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds
    
Backend Object
    :id: id of Backend
    :name: name of Backend
    :url: homepage of Backend
    :total_domains: total registered domains
    :tlds: list of TLD objects
    :total_tlds: total count of TLDs
    
TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :current_stage: name of current stage
    :domain_count: total count of registered domains in this TLD

Example
=======

Request

::

    GET /stats/backend/Donuts-Inc

Response

::

    {
        "resData": {
            "backend": {
                "id": "Donuts-Inc",
                "name": "Donuts Inc.",
                "url": "http:\/\/www.donuts.co",
                "total_domains": 1050611,
                "total_tlds": 152,
                "tlds": [{
                    "zone": "guru",
                    "zone_utf8": "guru",
                    "domain_count": 75685,
                    "current_stage": "GA"
                }]
            },
            "stats": {
                "total_domains": 3111803,
                "total_tlds": 431
            }
        },
        "code": 1000,
        "msg": "Command completed successfully"
    }

Sample Link: https://beta.api.ntldstats.net/stats/backend/Donuts-Inc

Registries Statistic
********************

Command
=======

**GET /stats/registries**

Arguments
    :limit: limit result to X tlds - default 30
    :details: if true, result contains details

Response
    :registries: list of Registry Objects
    :stats: total stats object

Total Stats Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds

Registry Object
    :id: id of Registry
    :name: name of Registry
    :url: homepage of Registry
    :total_domains: total registered domains
    :tlds: list of TLD objects (only on detailed listing)
    :total_tlds: total count of TLDs (only on detailed listing)
    
TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :current_stage: name of current stage
    :domain_count: total count of registered domains in this TLD
    
Example
=======

Request

::

    GET /stats/registries

Response

::

    {
        "resData": {
            "stats": {
                "total_domains": 3111803,
                "total_tlds": 431
            },
            "registries": [{
                "id": "XYZCOM-LLC",
                "name": "XYZ.COM LLC",
                "url": "http:\/\/nic.xyz",
                "total_domains": 706635
            }]
        },
        "code": 1000,
        "msg": "Command completed successfully"
    }

Sample Link: https://beta.api.ntldstats.net/stats/registries

Registry Statistic
******************

Command
=======

**GET /stats/registry/<id>**

Arguments
    :limit: limit result of tlds

Response
    :registry: Registry Object
    :stats: total stats object

Total Stats Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds
    
Registry Object
    :id: id of Registry
    :name: name of Registry
    :url: homepage of Registry
    :total_domains: total registered domains
    :tlds: list of TLD objects
    :total_tlds: total count of TLDs
    
TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :current_stage: name of current stage
    :domain_count: total count of registered domains in this TLD

Example
=======

Request

::

    GET /stats/registry/XYZCOM-LLC

Response

::

    {
        "resData": {
            "registry": {
                "id": "XYZCOM-LLC",
                "name": "XYZ.COM LLC",
                "url": "http:\/\/nic.xyz",
                "total_domains": 706635,
                "total_tlds": 2,
                "tlds": [{
                    "zone": "xyz",
                    "zone_utf8": "xyz",
                    "domain_count": 706634,
                    "current_stage": "GA"
                }]
            },
            "stats": {
                "total_domains": 3111803,
                "total_tlds": 431
            }
        },
        "code": 1000,
        "msg": "Command completed successfully"
    }

Sample Link: https://beta.api.ntldstats.net/stats/registry/XYZCOM-LLC

Parking Statistics by TLD
*************************

Command
=======

**GET /stats/parking/tld**

Arguments
    -- None

Response
    :stats: Global Statistic object
    :tlds: list of TLD objects

Global Statistic Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds
    :parking_domains: total count of parking domains
    :no_ns: total count of domains without nameservers
    :parking_ns: total count of domains with parking nameservers
    :no_record: total count of domains without A record
    :parking_ip: total count of domains with parking IP
    :private_ip: total count of domains resolving to private IPs
    :parking_check: total count of domains returning parking websites
    :http_error: total count of domains with HTTP errors
    :redirect: total count of domains returning redirect code

Statistic Object
    :parking_domains: total count of parking domains
    :no_ns: total count of domains without nameservers
    :parking_ns: total count of domains with parking nameservers
    :no_record: total count of domains without A record
    :parking_ip: total count of domains with parking IP
    :private_ip: total count of domains resolving to private IPs
    :parking_check: total count of domains returning parking websites
    :http_error: total count of domains with HTTP errors
    :redirect: total count of domains returning redirect code

TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :domain_count: total count of registered domains in this TLD
    :stats: Statistic Object
    
Example
=======

Request

::

    GET /stats/parking/tld

Response

::

    {
        "resData": {
            "stats": {
                "total_tlds": 431,
                "total_domains": 3111803,
                "parking_domains": 2056544,
                "no_ns": 11660,
                "parking_ns": 231350,
                "no_record": 486538,
                "parking_ip": 97615,
                "private_ip": 7198,
                "parking_check": 1222183,
                "http_error": 290152,
                "redirect": 281672
            },
            "tlds": [{
                "zone": "xyz",
                "zone_utf8": "xyz",
                "total_domains": 709096,
                "stats": {
                    "parking_domains": 485117,
                    "no_ns": 3356,
                    "parking_ns": 6015,
                    "no_record": 68129,
                    "parking_ip": 4329,
                    "private_ip": 3496,
                    "parking_check": 399792,
                    "http_error": 105986,
                    "redirect": 20461
                }
            }],
            "code": 1000,
            "msg":"Command completed successfully",
        }
    }

Sample Link: https://beta.api.ntldstats.net/stats/parking/tld

Parking Statistics by Registrar
*******************************

Command
=======

**GET /stats/parking/registrar**

Arguments
    -- None

Response
    :stats: Global Statistic object
    :registrars: list of Registrar objects

Global Statistic Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds
    :parking_domains: total count of parking domains
    :no_ns: total count of domains without nameservers
    :parking_ns: total count of domains with parking nameservers
    :no_record: total count of domains without A record
    :parking_ip: total count of domains with parking IP
    :private_ip: total count of domains resolving to private IPs
    :parking_check: total count of domains returning parking websites
    :http_error: total count of domains with HTTP errors
    :redirect: total count of domains returning redirect code

Statistic Object
    :parking_domains: total count of parking domains
    :no_ns: total count of domains without nameservers
    :parking_ns: total count of domains with parking nameservers
    :no_record: total count of domains without A record
    :parking_ip: total count of domains with parking IP
    :private_ip: total count of domains resolving to private IPs
    :parking_check: total count of domains returning parking websites
    :http_error: total count of domains with HTTP errors
    :redirect: total count of domains returning redirect code

Registrar Object
    :id: id of Registrar
    :iana_id: registrar IANA id
    :name: name of Registrar
    :url: homepage of Registrar
    :registrar_group: Registrar Group object
    :total_domains: total registered domains
    :stats: Statistic object
    
Registrar Group Object
    :name: name of Registrar Group
    :url: homepage of Registrar Group

Example
=======

Request

::

    GET /stats/parking/registrar

Response

::

    {
        "resData": {
            "stats": {
                "total_tlds": 431,
                "total_domains": 3111803,
                "parking_domains": 2056544,
                "no_ns": 11660,
                "parking_ns": 231350,
                "no_record": 486538,
                "parking_ip": 97615,
                "private_ip": 7198,
                "parking_check": 1222183,
                "http_error": 290152,
                "redirect": 281672
            },
            "registrars": [{
                "total_domains": 413708,
                "id": "2-Network-Solutions-LLC",
                "iana_id": "2",
                "name": "Network Solutions, LLC",
                "registrar_group": {
                    "name": "Web.com",
                    "url": "https:\/\/www.web.com\/"
                },
                "stats": {
                    "parking_domains": 397980,
                    "no_ns": 37,
                    "parking_ns": 145,
                    "no_record": 16088,
                    "parking_ip": 6,
                    "private_ip": 28,
                    "parking_check": 381676,
                    "http_error": 11376,
                    "redirect": 2953
                }
            }],
            "code": 1000,
            "msg":"Command completed successfully",
        }
    }

Sample Link: https://beta.api.ntldstats.net/stats/parking/registrar

Parking Statistics by TLD
*************************

Command
=======

**GET /stats/parking/tld**

Arguments
    -- None

Response
    :stats: Global Statistic object
    :tlds: list of TLD objects

Global Statistic Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds
    :parking_domains: total count of parking domains
    :no_ns: total count of domains without nameservers
    :parking_ns: total count of domains with parking nameservers
    :no_record: total count of domains without A record
    :parking_ip: total count of domains with parking IP
    :private_ip: total count of domains resolving to private IPs
    :parking_check: total count of domains returning parking websites
    :http_error: total count of domains with HTTP errors
    :redirect: total count of domains returning redirect code

Statistic Object
    :parking_domains: total count of parking domains
    :no_ns: total count of domains without nameservers
    :parking_ns: total count of domains with parking nameservers
    :no_record: total count of domains without A record
    :parking_ip: total count of domains with parking IP
    :private_ip: total count of domains resolving to private IPs
    :parking_check: total count of domains returning parking websites
    :http_error: total count of domains with HTTP errors
    :redirect: total count of domains returning redirect code

TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :domain_count: total count of registered domains in this TLD
    :stats: Statistic Object
    
Example
=======

Request

::

    GET /stats/parking/tld

Response

::

    {
        "resData": {
            "stats": {
                "total_tlds": 431,
                "total_domains": 3111803,
                "parking_domains": 2056544,
                "no_ns": 11660,
                "parking_ns": 231350,
                "no_record": 486538,
                "parking_ip": 97615,
                "private_ip": 7198,
                "parking_check": 1222183,
                "http_error": 290152,
                "redirect": 281672
            },
            "tlds": [{
                "zone": "xyz",
                "zone_utf8": "xyz",
                "total_domains": 709096,
                "stats": {
                    "parking_domains": 485117,
                    "no_ns": 3356,
                    "parking_ns": 6015,
                    "no_record": 68129,
                    "parking_ip": 4329,
                    "private_ip": 3496,
                    "parking_check": 399792,
                    "http_error": 105986,
                    "redirect": 20461
                }
            }],
            "code": 1000,
            "msg":"Command completed successfully",
        }
    }

Sample Link: https://beta.api.ntldstats.net/stats/parking/tld

Fraud Statistics
****************

Command
=======

**GET /stats/fraud**

Arguments
    :limit: limit result to X tlds - default 1000
    :details: if true, result contains items list
    :no_nameserver: default true, skip entries without nameservers
    :no_dns_hold: default true, skip entries with dns hold flag
    :has_dns_record: default true, skip entries without dns records
    :no_resolving_ns: default true, skip entries with "non-resolver-nameserver"

Response
    :stats: Global Statistic object
    :lists: list of Blacklist List objects
    :tlds: list of TLD Statistic objecs
    :items: list of Blacklist Entry objects (optional)

Global Statistic Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds
    :total_fraud_domains: total count of suspicious domains
    :total_dnsbl_domains: total count of domains in dnsbl lists
    :total_dnsbl_lists: total count of dnsbl lists
    :total_gsb_domains: total count of domains in gsb lists
    :total_gsb_lists: total count of gsb lists

TLD Statistic Object
    :count: total count ot suspicious domains
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language

Blacklist List Object
    :id: id of blacklist item
    :name: name of blacklist
    :url: url of blacklist
    :dnshost: blacklist hostname (optional)
    :total_active_records: total count of suspicious domains  (optional)

Blacklist Entry Object
    :created: date entry added to database
    :domain_name: name of domain, idn encoded
    :domain_name_utf8: name of domain in native language
    :tld: name of tld, idn encoded
    :tld_utf8: name of tld in nativ language
    :country: iso country code owner contact
    :lists: list of Blacklist List Object
    :additional_info: additional infos returned by blacklist
    :additional_link: additional link returned by blacklist
    :has_nameserver: domain has linked nameservers
    :has_dns_hold: dns hold flag is set for domain
    :has_dns_record: domain nameserver answered with valid A record

Example
=======

Request

::

    GET /stats/fraud

Response

::

    {
        "resData": {
            "stats": {
                "total_domains": 3631218,
                "total_tlds": 436,
                "total_fraud_domains": 1696,
                "total_dnsbl_domains": 2,
                "total_dnsbl_lists": 29,
                "total_gsb_domains": 2,
                "total_gsb_lists": 4
            },
            "lists": {
                "dnsbl": [{
                    "id": 328,
                    "name": "abuse.ch ZeuS Tracker Domain",
                    "url": "https:\/\/zeustracker.abuse.ch\/",
                    "dnshost": "uribl.zeustracker.abuse.ch",
                    "total_active_records": 0
                }],
                "gsb": [{
                    "id": 1,
                    "name": "Google Safe Browsing Phishing",
                    "url": "https:\/\/developers.google.com\/safe-browsing\/safebrowsing_faq",
                    "total_active_records": 15
                }, {
                    "id": 2,
                    "name": "Google Safe Browsing Malware",
                    "url": "https:\/\/developers.google.com\/safe-browsing\/safebrowsing_faq",
                    "total_active_records": 82
                }, {
                    "id": 3,
                    "name": "Yandex Safe Browsing Phshing",
                    "url": "http:\/\/api.yandex.com\/safebrowsing\/",
                    "total_active_records": 0
                }, {
                    "id": 4,
                    "name": "Yandex Safe Browsing Malware",
                    "url": "http:\/\/api.yandex.com\/safebrowsing\/",
                    "total_active_records": 12
                }]
            },
            "tlds": [{
                "count": 806,
                "zone": "link",
                "zone_utf8": "link"
            }],
            "items": {
                "dnsbl": [{
                    "created": "2014-12-27T08:02:33Z",
                    "additional_info": "",
                    "domain_name": "kino",
                    "tld": "menu",
                    "country": "CA",
                    "domain_name_utf8": "kino",
                    "tld_utf8": "menu",
                    "lists": [{
                        "name": "Spamhaus DBL Domain Block List",
                        "url": "http:\/\/www.spamhaus.org\/dbl\/",
                        "id": 575
                    }],
                    "additional_link": "http:\/\/www.spamhaus.org\/query\/dbl?domain=kino.menu",
                    "has_nameserver": true,
                    "has_dns_hold": false,
                    "has_dns_record": true
                }],
                "gsb": [{
                    "created": "2014-12-28T04:21:10Z",
                    "additional_info": "",
                    "domain_name": "starradio",
                    "tld": "london",
                    "country": "GB",
                    "domain_name_utf8": "starradio",
                    "tld_utf8": "london",
                    "lists": [{
                        "name": "Google Safe Browsing Malware",
                        "url": "https:\/\/developers.google.com\/safe-browsing\/safebrowsing_faq",
                        "id": 2
                    }],
                    "additional_link": "https:\/\/safebrowsing.clients.google.com\/safebrowsing\/diagnostic?site=starradio.london",
                    "has_nameserver": true,
                    "has_dns_hold": false,
                    "has_dns_record": true
                }]
            }
        },
        "code": 1000,
        "msg": "Command completed successfully"
    }

Sample Link: https://beta.api.ntldstats.net/stats/fraud

.. _nTLDStats: http://ntldstats.com
