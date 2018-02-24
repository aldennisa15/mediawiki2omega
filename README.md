# mediawiki2omega
dump a MediaWiki database into a form suitable for indexing into a Xapian database using scriptindex

# mediawki2omega quick howto ...

- edit $wgXxxx variables to match MediaWiki LocalSettings.php (e.g. /etc/mediawiki/LocalSettings.php)
- dump MediaWiki to file : ./mediawiki2omega > mediawiki.dump
- index dump into xapian/omega : scriptindex /var/lib/xapian-omega/data/default mediawiki.script mediawiki.dump
- add daily cron entry just after midnight for yesterdays updates, e.g. 5 0 \* \* \* mediawiki2omega --cron > mediawiki.dump;scriptindex ...

# limitations

- only dumps Main namespace, not Talk:, User: etc namespaces
- assumes wiki, database and xapian/omega are all on the localhost machine
