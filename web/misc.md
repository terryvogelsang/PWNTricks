# Misc


## MySQL Default max_packet_size

In its default configuration, MySQL only accepts packets that <16MB. If we're sending a packet that exceeds this size, the packet will be dropped, and the query will fail.