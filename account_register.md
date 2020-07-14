# Save for later write new cms for wow
- How hashed pass are generated
```
<?php

$username = "q@q";
$password = "q";
$hashed = sha1(strtoupper($username).":".strtoupper($password));

echo "hashed for account: ";
echo strtoupper($hashed);
echo "\n";
        
$bnet_hashed_pass = strtoupper(bin2hex(strrev(hex2bin(strtoupper(hash('sha256', strtoupper(hash('sha256', strtoupper($username)) . ':' . strtoupper($password))))))));

echo "hashed for bnet: ";
echo strtoupper($bnet_hashed_pass);
```

output
```
hashed for account: 455DB77697463A265E5E6E74DC573D7901563BA9
hashed for bnet: D8AF8C48C208923B8FBCC34A66353502B9D078B3FB42BF2281440DF6642A2CF4
```

Test in here: https://sandbox.onlinephpfunctions.com/
