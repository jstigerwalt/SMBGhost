# SMBGhost

Python script contains 3 seperate packet payloads.

1. Request <- Start SMB session communication
2. Session <- Session information, neogation 
3. SMB3 <- SMB3 compression (This is where we send bad offset)

May need to execute the script multiple times, there is no pause or recv check done. 

