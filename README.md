# ncs_deduplication

Goal: To improve the effeciency of memory utilization in NSO

![image](https://user-images.githubusercontent.com/1794046/183038880-bd72905d-a205-404f-91cf-cd179b0c8ab1.png)
On my left conserding each row as device configuration, which can be deduplicated in NCS DB.

- [ ] Need to understand how NCS DB is works
- [ ] Need to locate the duplicate device configuration (blocks) from all devices
- [ ] To apply deduplication technique
- [ ] Need to check the stats and imporvements on this approach


Network Configuration deduplication:
- [ ] mapping block to devices and ref. counts
     - [ ] global blocks
     - [ ] child blocks
```
interface GigabitEthernet0/1/3
 no switchport
 negotiation auto
 no ip address
 shutdown
exit
interface GigabitEthernet0/1/4
 no switchport
 negotiation auto
 no ip address
 shutdown
exit
interface GigabitEthernet0/1/5
 no switchport
 negotiation auto
 no ip address
 shutdown
exit
....
```
can be translated to deduplication
```python
{
"Refcount": 3
"Hash": 
     {
     "no switchport": None,
     "negotiation auto": None,
     "no ip address": None,
     "shutdown": None,
     "exit": None
     }
}

interface GigabitEthernet0/1/3
 expand(Hash)
interface GigabitEthernet0/1/4
 expand(Hash)
interface GigabitEthernet0/1/5
 expand(Hash)
```

the translation I used here is from shconfparser where the device configuration is converted to JSON
- Creating a block as shown in above
- Refering them in the actual configuration this will save a lot a memory across all the devices imported to NSO

## TODO
- need to read more about deduplication methodology 
- need to read more about it's techniques and existing algorithms.
