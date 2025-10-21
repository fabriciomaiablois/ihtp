# ihtp

## Configure GitHub Page

Create A records for apex domain in Namecheap Advanced DNS panel for the domain(in this example, the fictional  "example.com"):

|Record Type|Host|Address|TTL|
|-----------|----|-------|----|
|A Record| @ | 185.199.108.153 | 30 minutes|
|A Record| @ | 185.199.109.153 | 30 minutes|
|A Record| @ | 185.199.110.153 | 30 minutes|
|A Record| @ | 185.199.111.153 | 30 minutes|
|CNAME Record| www | youracctname.github.io | 30 minutes|

Wait an hour, then test if DNS is set up properly:
```
me@myhost:~$ dig +noall +answer +nocmd example.com
example.com.		1800	IN	A	185.199.110.153
example.com.		1800	IN	A	185.199.109.153
example.com.		1800	IN	A	185.199.108.153
example.com.		1800	IN	A	185.199.111.153
```

```
me@myhost:~$ dig +noall +answer +nocmd www.example.com
www.example.com.	1800	IN	CNAME	youracctname.github.io.
youracctname.github.io.	3600	IN	A	185.199.108.153
youracctname.github.io.	3600	IN	A	185.199.111.153
youracctname.github.io.	3600	IN	A	185.199.110.153
youracctname.github.io.	3600	IN	A	185.199.109.153
```

In the GitHub repo config for Pages (Settings... Pages), enter your apex domain, "example.com" (not "www.example.com") in the "Custom Domain" box.

Wait for GitHub to generate and install the SSL certificate for that apex domain (at least an hour).

Test by going to "https://example.com" and "https://www.example.com".