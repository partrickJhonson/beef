## Metasploit payloads

Once [[configured|Configuration]] and launched, Metasploit payloads are directly included in the BeEF modules :
[[Images/msf2.png|align=center]]

When selecting a payload, all options of metasploit modules can be direclty given in the BeEF web interface :

[[Images/msf3.png|align=center]]

You then just have to wait for the exploit to work :

[[Images/msf6.png|align=center]]

## Metasploit autopwn

While the feature is not directly integrated in BeEF, you can easily use the autopwn function of metasploit with BeEF. First, launch autopwn in metasploit and get the autopwn URL (for example here http://10.1.1.1:8080/ytX55lnb47HTz ) :

[[Images/msf7.png|align=center]]

Then use the "Create invisible iframe" payload to redirect the browser to the autopwn webpage :

[[Images/msf8.png|align=center]]

You just have to wait for a shell :

[[Images/msf9.png|align=center]]

***

[[Previous|Network-discovery]] | [[Next|Tunneling]] 