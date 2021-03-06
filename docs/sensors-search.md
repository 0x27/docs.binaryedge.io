# Sensors Search Parameters

The API has endpoints for querying our data in which you can use free text search together with one or more of the filters listed below.

**NOTE** : Although free text search without specifying fields is available, it is processed differently from searching on specific fields. For better results, always specify search fields.


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

### as_name: (string)
Search by AS name. 

    e.g. as_name:amazon

### tags: (string)
Search by tags.

    e.g. tags:NMAP_SCANNER

#### Available tags

* AMPEREINNOTECH
* AMPLIFICATION
* ASTERISK_SCANNER
* BACKDOOR
* BAIDUSPIDER
* BINARYEDGE
* BENIGN
* BINGBOT
* BITSIGHT
* BOTNET
* CENSYS
* CISCO_SMART_INSTALL
* CODESYS_SCANNER
* CRYPTOCURRENCY_SCANNER
* CVE-2017-17215
* DICT_SCANNER
* DLINK_SCANNER
* DRUPAL_SCANNER
* DUCKDUCKBOT
* ELASTICSEARCH_SCANNER
* EMAIL_SCANNER
* EMOTET
* EOS_NODE_SCANNER
* ETHEREUM_NODE_SCANNER
* EXABOT
* EXPLOITATION
* FACEBOOKEXTERNALHIT
* FINGER_SCANNER
* FOX_SCANNER
* FTP_SCANNER
* GIT_SCANNER
* GOODOR
* GOOGLEBOT
* GPON_ONT_SCANNER
* HADOOP_HDFS_SCANNER
* HADOOP_YARN_SCANNER
* HTTP_CRAWLER
* HTTP_SCANNER
* HUAWEI_HG532_SCANNER
* INTERNET_CENSUS
* IPFIRE_EXPLOIT
* IS_ARCHIVER
* JABBER_SCANNER
* JANUARY
* JAVA_SCANNER
* JUNIPER_SCANNER
* KGUARD_SCANNER
* MALICIOUS
* MALWARE
* MEMCACHED_SCANNER
* MICROSOFT_SQL_SERVER
* MODBUS_SCANNER
* NETSYSTEMS
* NMAP_SCANNER
* NUUO_NVR_SCANNER
* ONYPHE
* ORACLE_TNS_SCANNER
* PEPPA
* PHPMYADMIN
* PRINTER_SCANNER
* PROJECT25499
* PUTTY_CLIENT
* RADWARE_SCANNER
* RAPID7
* RDP_SCANNER
* REDIS_SCANNER
* RFB_SCANNER
* ROUTER_SCANNER
* RSYNC_SCANNER
* RTSP_SCANNER
* SAP_SCANNER
* SCADA_SCANNER
* SEZNAM
* SHADOWSERVER
* SHODAN
* SIP_SCANNER
* SLURP
* SMB_SCANNER
* SOGOU
* SOURCE_ENGINE
* SSH_SCANNER
* SSL_SCANNER
* TOR
* TOR_SCANNER
* TRICKBOT
* UBIQUITI_SCANNER
* UPNP_SCANNER
* VNC_SCANNER
* WORDPRESS_SCANNER
* YANDEXBOT
* ZGRAB_SCANNER
* ZTE_F460_SCANNER
* ZTE_F660_SCANNER

### created_at: (date)
Search by timestamp.

    e.g.
        created_at:[2018-09-01 TO 2018-10-01]
        created_at:2018-09-01

### rdns: (string)
Search by RDNS.

    e.g. rdns:static-206-162-231-219.wireless.unwiredbb.net

### rdns_parent: (string)
Search by RDNS root.

    e.g. rdns_parent:unwiredbb.net

### extra.http.path: (string)
Search by HTTP path.

    e.g. extra.http.path:"/index.html"

### extra.http.method: (string)
Search by HTTP method.

    e.g. extra.http.path:POST

### extra.http.headersFull: (string)
Search by HTTP headers:

    e.g. extra.http.headersFull:google

### extra.ssh.description: (string)
Search by SSH identification string.

    e.g. extra.ssh.description:dropbear

### extra.ssh.hassh: (string)
Search by HASSH hash.

    e.g. extra.ssh.hassh:92674389fa1e47a27ddd8d9b63ecd42b

### extra.ssh.hassh_algorithms: (string)
Search by HASSH algorithms string.

    e.g. extra.ssh.hassh_algorithms:"diffie-hellman-group14-sha1,diffie-hellman-group-exchange-sha1,diffie-hellman-group1-sha1;aes128-ctr,aes192-ctr,aes256-ctr,aes256-cbc,rijndael-cbc@lysator.liu.se,aes192-cbc,aes128-cbc,blowfish-cbc,arcfour128,arcfour,cast128-cbc,3des-cbc;hmac-sha1,hmac-sha1-96,hmac-md5,hmac-md5-96,hmac-ripemd160,hmac-ripemd160@openssh.com;none"

### extra.ssl.ja3: (string)
Search by JA3 string.

    e.g. extra.ssl.ja3:"771,49200-49196-49192-49188-49172-49162-165-163-161-159-107-106-105-104-57-56-55-54-136-135-134-133-49202-49198-49194-49190-49167-49157-157-61-53-132-141-49199-49195-49191-49187-49171-49161-164-162-160-158-103-64-63-62-51-50-49-48-154-153-152-151-69-68-67-66-49201-49197-49193-49189-49166-49156-156-60-47-150-65-140-49169-49159-49164-49154-5-4-138-255,0-11-10-35-13-15-21,23-25-28-27-24-26-22-14-13-11-12-9-10,0-1-2"

### extra.ssl.ja3_digest: (string)
Search by JA3 hash.

    e.g. extra.ssl.ja3_digest:85ceddf7e8f7ad69d40c81c05e0fde96


## Notes

**Free Text**: not specifying a field will search on the full records, which can include other information not stated above.

**Conditionals**: the following conditionals are available: NOT, AND, OR. Must be UPPERCASE. You can also use the minus sign (-) as a replacement for the NOT conditional.

**Comparison**: you can use comparison operators on number fields. E.g. _field:>100.

**String fields caveat**: if the string is expected to have spaces, some kind of punctuation in the middle, or special symbols, instead of querying _field:value_ try _field:"value"_. You can also try instead _field.keyword:"value"_. The first one will search for any occurrence of any of the words in _value_, while the second one will search for an exact match of the string.

**Field existence or omission**: you can search for records that have a specific field by using _\_exists\_:field_. Conversely, for records missing a field it would be _NOT \_exists\_:field_.
