# ncs_deduplication

This research is for effective utilization of NSO memory (RAM) on storing the network devices data

- [ ] Need to understand how NCS DB is working
- [ ] Need to locate the duplicate blocks from all devices
- [ ] When identified new need to apply deduplication technique
- [ ] stats on this methodology

Deduplication Technique
- [ ] mapping block to devices and ref. counts
     - [ ] global blocks
     - [ ] child blocks


===> recent techniques, currently thinking
--> translating the running config to JSON (shconfparser) --> Need to validate the Space on converting this approach. 
--> inside of keys if we find expand(Hash) --> it's deduplicated, collect and replace it
--> deduplicate blocks need to have (Hash, configuration)

===> need to read a lot about the deduplication methology and it's algorithms
