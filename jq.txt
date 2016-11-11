### rackspace json
curl -s  -H "X-Auth-Token: notreal" https://iad.servers.api.rackspacecloud.com/v2/<account>/servers/detail?name=test  |  jq '.servers[].id' | sort | uniq | wc -l

|  jq '.servers[] | {"name": .name, "id": .id}'
|  jq '.servers[] | .name,.id'
| jq '.[] | to_entries[]'

cat servers.txt  | while read i; do curl -s -H "X-Auth-Token: notreal" https://iad.servers.api.rackspacecloud.com/v2/<account>/servers/$i | jq .server.id,.server.name,.server.created; echo; echo; echo; done > servers_details.txt
