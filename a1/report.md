# Questions

**What is the password of the container?**   
The password for the container "container\_12541897.hc" with hash,
770be38a44dcbd4e4c5dce5d8b9031bc3b41029cfe2f37530d6091e73b1f1e1f, is: 
"i1cv".

**What is the “secret” in the container?**   
The secret in the container is a .txt file called secreth with the
followig key inside:
55bfe819583065d096e10f49c86747ae4e3b87e9a7

**What was saved in the container by Spongebob?**   
awesome.jpg  secret.txt  trippin.jpg  wasted.jpg
He had three images and a txt file with the secret key.

**How much time is needed for brute forcing different password lengths and
character sets?**   
Using hashcat in my machine, GeForce RTX 3050 Ti Mobile, and doing the scan
in a bench in the street of Vienna, so my laptop does not overheat, I
managed to get an average of 670 H/s. This is taking into account that the
algorithm I am trying to break is sha256, which highly affects the speed,
it is a very slow algorithm to break.

Assuming english alphabet, 26 letters, 10 digits and 32 special characters
the worst-case (for the hacker) scenario to break a sha256 hash looks 
like this:

    Digits  LowerCase   UpperCase   Numbers   SpecialChars    Time
-----------------------------------------------------------------------
      4        yes         yes        no           no         3,04    h 
      4        yes         yes        yes          no         6,13    h
      4        yes         yes        yes          yes        1,4     d 
      6        yes         yes        no           no         342     d 
      6        yes         yes        yes          no         2,69    y 
      6        yes         yes        yes          yes        32,7    y
      8        yes         yes        no           no         2530    y
      8        yes         yes        yes          no         10334   y
      8        yes         yes        yes          yes        288.497 y


**What password complexity is needed for a 10-year secure container?**


------------------------

# Report
## Factual part
On the 13 of April 2026 I started my work on the container 
"container\_12541897.hc", property of Spongebob Squarepants. All work was
conducted under a machine with:
Under a system with:
```bash
Ubuntu 24.04.4 LTS
```
The hashed value of the container before starting any work is:
```bash
770be38a44dcbd4e4c5dce5d8b9031bc3b41029cfe2f37530d6091e73b1f1e1f  container\_12541897.hc
```
This value was obtained using the tool:
```bash
sha256sum (GNU coreutils) 9.4
```
Before prociding I made a copy of the container and worked on that copy.
It was also verified that the copy did not modified any data by calculating
the hash again:
```bash 
770be38a44dcbd4e4c5dce5d8b9031bc3b41029cfe2f37530d6091e73b1f1e1f  container\_12541897.hc
770be38a44dcbd4e4c5dce5d8b9031bc3b41029cfe2f37530d6091e73b1f1e1f  container\_12541897\_copy.hc
```
Now it is possible to start. The task that was given to me was to crack the
password of the container. Every veracrypt container has it's password 
stores in the first 512 btyes of the container (you can think of a byte as 
an unit of information). In order to decrypt the container I need to get 
that password. The python tool "veracrypt2hashcat.py" was used for that
purpose, because there is no version control for this tool, it will be
uploaded with the report. The hashed value of the tool is:
```bash
bd65dedb60e7b15a620f6b0a3f83b12747d21c4cf8f6968073f5427203e75119  veracrypt2hashcat.py
```
However, extracting the pasword from the container is not enough, because
it is hashed, it is impossible to read it. The hashed password looks like
this:
```bash
$veracrypt$ad01d525e3ae9059d408ef54ffcc6f7c3a6a027a9a4ee5c13dce4879be733dd08138ed1b95560a03b007f194b790a573e33afb34da6bbf03ce621335c798a005$d58ad8331d8f8a8c8af9a6117dfe17faebc6e3618c41865d97119ae4669f4632205033209ca2083fb91081487e17917f6cfcbf9dc7f93bb1e0de7c45c19bf5c116a0e7a1f3c1b2eaa01cfc912f591ec1248ea25cf37e382349218307ccc92856bd2c8ff78fdf8363531916e22d74abe527236e8ce4cee0f005317d437bfe3a6ea721523196f481c3472cbedb5523f467efa7c60a39f1202c6e9222b380a09c4e11cf666cfe614614acbf40225caa03a1630364f36ab83d2b2f62712092a882528c19e5487722c58f7de0ffdeef7cfd67bbd2677f3dd743f684c37c704405c3a7ba594cf323a640eea1c82703741095fdc7f43107152856d560b7601be979210948d747f8e5f2572e4cead453928372a7844b62eb76d7a6c3db3e2718f6481db6d16658f18b849d882a7a38c07a043bc45ba829a0cb09cb76296390d4f967e149c06541ae8a7adc70fc03af00b356b812bb8455381ef2ee65e9267a3457a63ba6f1ae83e254c3f89adfa9bff9ce0735a0d2724c77a852e2a98254a2e89627769b5294dc264043119199cec04af5b7d4aa37d4a91c311a7aeeab4a1454f458df9e36145132d10244e6a1d572c3033e1bf38a11fcc70b6f2c888303d817848ec8d7
```
The tool used to crack the password is hashcat:
```bash
v6.2.6
```
The mask used contained all the english alphabet letters in lowercase and
uppercase, it also contained all 10 digits (0..9). The password is known
to be 4 digits long.

After 1h 5min the hash is cracked and the password is:
```bash
i1cv
```
The container can now be mounted. The contents found are:
```bash
362372 Apr 11 17:35 awesome.jpg
7d8355b740c5f07e4c4ed682374867dbbcd7921297bb6139a59d36ed94575949  awesome.jpg

42 Apr 11 17:35 secret.txt
7710484656d0529169bca758cbaf8c862ff1d78c8d7c5ec1091ad066e8b8da80  secret.txt

80961 Apr 11 17:35 trippin.jpg
c21c67ec7d1c9e7a8c397acb68dd36af82b119ad1fe2a3c1d03cfacd1b433b3a  trippin.jpg

98374 Apr 11 17:35 wasted.jpg
1a560c55c7b7c59882713876cf9460773451cf277621deb36cf9d65ed297a4f9  wasted.jpg
```

Finally, the copy is hashed again to verify that nothing has being
modified.
```bash
770be38a44dcbd4e4c5dce5d8b9031bc3b41029cfe2f37530d6091e73b1f1e1f  container\_12541897\_copy.hc
```

## Expert testimony
answers the specific questions
includes expert interpretation



secret in veracrypt container: 55bfe819583065d096e10f49c86747ae4e3b87e9a7
