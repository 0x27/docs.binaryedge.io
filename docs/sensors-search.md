# Sensors Search Parameters

The API has endpoints for querying our data in which you can use free text search together with one or more of the following filters:

## Notes

**Free Text**: not specifying a field will search on the full records, which can include other information not stated above.

**Conditionals**: the following conditionals are available: NOT, AND, OR. Must be UPPERCASE. You can also use the minus sign (-) as a replacement for the NOT conditional.

**String fields caveat**: if the string is expected to have spaces or some kind of punctuation in the middle, instead of querying _field:value_ try instead _field.keyword:"value"_. The first one will search for any occurrence of any of the words in _value_, while the second one will search for an exact match of the string.

**Field existence or omission**: you can search for records that have a specific field by using _\_exists\_:field_. Conversely, for records missing a field it would be _NOT \_exists\_:field_.

## Fields

### ip: (string) 
Search by IP address or CIDR. 

    e.g ip:"192.168.1.1/24" or ip:192.168.1.1

### port: (int) 
Search by target port number. 
    
    e.g. port:80

### payload: (string) 
Search in the payloads for a specific string
    
    e.g. payload:wget

### country: (string) 
Search using ISO2 Country Codes. 
    
    e.g. country:ES

### geoip.country_name: (string) 
Search using country names. 
    
    e.g. geoip.country_name:spain

### geoip.city_name: (string) 
Search using city names. 
    
    e.g. geoip.city_name:madrid

### asn: (int)
Search by ASN. 

    e.g. asn:4812

### tags: (string)
Search by tags.

```
    e.g. tags:mobile
```

Can be:

  * ETHEREUM_NODE_SCANNER
  * VNC_SCANNER
  * PHPMYADMIN
  * VOIP_SCANNER
  * ADB_SCANNER
  * NMAP_SCANNER
  * ORACLE_TNS_SCANNER
  * RSYNC_SCANNER
  * WORDPRESS
  * SHODAN
  * CENSYS
  * RAPID7
  * SHADOWSERVER


### created_at: (date)
Search by timestamp.

Examples:

    created_at:[2018-09-01 TO 2018-10-01]
    created_at:2018-09-01