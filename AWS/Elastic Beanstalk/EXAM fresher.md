 - So important that you cant put/post/option/delete in Cloudfront cahce.
 So basically, any of those wont be saved to cache.
 - USer- generated videos, means user already generated and put them in the origin, anytime you access this user generated data, its gonna be cached.
What you need to remember is, any data that is **prone to changes** is not cached.
- therefore, dynamic request time data is not stored.
- anything specifycally configured iisde the distribution or configuration of cloudfront that youve created will not be stored in cache.
this statement, example:
'You configured CloudFront to forward all headers (to handle cookies and tokens).'
means that in the distribution youve configured to forward all headers. And header are what includes cookies, token and sensitive data which will be used for computation purposes, which cant be saved in cache and needs to be sent to origin.
EX:
The page `example.com/dashboard` shows personalized info:
- Your **name**
- Your **shopping cart**
- Your **past orders**
This content **changes based on who is logged in**.

When a user logs in, their browser sends **HTTP headers** like:
- `Authorization` (contains login token)
- `Cookie` (session data)
- `User-Agent` (browser info)
These headers **change for each user**.
So, if you tell CloudFront:
> “Hey, forward all headers to the origin!”
CloudFront says:
> “Oh, I can’t cache this. Too risky! Every user might get different data!”
➡️ So it **does NOT cache** the response.
➡️ It **sends the request to your main server every time**.

---

