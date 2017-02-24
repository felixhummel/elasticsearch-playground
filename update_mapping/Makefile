# ES 5 removed strings and replaced them with text and keyword.
# https://www.elastic.co/blog/strings-are-dead-long-live-strings
#
# Given an existing mapping with text fields, can we add keyword fields for them retroactively?

# foo/user with a text property called "name"
old:
	curl -XPUT 'http://localhost:9200/foo' -d @old.json 
data:
	curl -XPOST 'http://localhost:9200/foo/user/_bulk?pretty' --data-binary "@data.json" 

show_mapping:
	curl 'http://localhost:9200/foo/_mapping?pretty'

# this should be empty
search_term:
	curl -XPOST 'http://localhost:9200/foo/user/_search?pretty' -d @search_term.json
search_match:
	curl -XPOST 'http://localhost:9200/foo/user/_search?pretty' -d @search_match.json
# update the mapping, so "name" gets a sub-property called "keyword"
new:
	curl -XPUT 'http://localhost:9200/foo/user/_mapping' -d @new.json 

search_keyword_term:
	curl -XPOST 'http://localhost:9200/foo/user/_search?pretty' -d @search_keyword_term.json
search_keyword_match:
	curl -XPOST 'http://localhost:9200/foo/user/_search?pretty' -d @search_keyword_match.json

delete_index:
	curl -XDELETE 'http://localhost:9200/foo'

