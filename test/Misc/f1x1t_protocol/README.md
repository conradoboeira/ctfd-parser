# f1x1t protocol

**Category** : Misc
**Points** : 600

f1x1t protocol


We hunted down a cybercrime ring known as sixpaths.
During analysis of a seized binary, we discovered that the adversary relied on a custom application‑layer protocol named f1x1t() to communicate with their command server. Their packets looked like this:

f1x1t() / UDP / IP / ETH


The malware attempted to evade network monitoring by using a protocol format that traditional tools would not decode without custom parsers. We recreated a miniature version of f1x1t() for you to analyze.

Your task is to recreate an f1x1t packet exactly as the server expects and send it to the challenge server. Only a perfectly constructed packet will reveal the flag
the packet specification is as follow


  MT      1 byte    = 0x03
  TOKLEN  1 byte
  TOKEN   TOKLEN bytes
  TS      4 bytes             # unix timestamp (seconds)
  FLAGS   1 byte              # must equal 0x5A
  SEQ     2 bytes             # client-chosen sequence number
  PLEN    2 bytes             # length of PAYLOAD 
  PAYLOAD PLEN bytes          # maximum 32 bytes
  HMAC    32 bytes            # HMAC-SHA256(key=token_raw_bytes, data=MT..PAYLOAD)



