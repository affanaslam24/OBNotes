![[Screenshot from 2025-04-09 11-20-22.png]]
- lets suppose the first user asked for an object, and the object gets cached in edge location.
- now the object is changed inside the bucket, with the same name.
- But the object called in the edge location will not be updated **until the TTL expires or the object goes stale**
- Now what would happen in that case?
![[Screenshot from 2025-04-09 11-20-32.png]]
- customer 2 accessing the object through edge will see the wrong object stored in edge, because the TTL hasnt expired and there is no way to remove it without using special features.

But after the TTL expires:
![[Screenshot from 2025-04-09 11-21-38.png]]
the edge location will check with the origin, and will give 304 if its not modified witht the newer model of the picture.
- and the newest customer requesting the edge will see a new image.

![[Screenshot from 2025-04-09 11-24-47.png]]
- defualt TTL value is 24hrs.
- you can set max and min TTL values
- the origin headers can ignore, but its basically how many times the caching will happen from the origin.
- 2 are in seconds.
- one is in fixed date or time.

##### To explain minimm and maximum cache and the headers for origin, we will see this example:

 TTL Settings Explained

| Setting         | What It Means                                                                           |
| --------------- | --------------------------------------------------------------------------------------- |
| **Minimum TTL** | The **shortest time** CloudFront will cache an object, even if headers say otherwise    |
| **Maximum TTL** | The **longest time** CloudFront will cache an object, even if headers say otherwise     |
| **Default TTL** | Used when the origin does **not** send any caching headers (`Cache-Control`, `Expires`) |

### **Minimum TTL**

- If your origin says "cache this for 10 seconds", but you set **Minimum TTL = 60**, CloudFront will **still cache it for 60 seconds**.
- Useful when you **want to reduce traffic to your origin**, even if origin headers are too aggressive.
---

### 🔸 **Maximum TTL**

- If your origin says "cache this for 10 years", but you set **Maximum TTL = 1 day**, CloudFront will **only cache it for 1 day**.
- This protects you from overly long cache durations that may cause **stale content**.

---

### 🟡 **Default TTL**

- Used **when the origin doesn't send any cache headers**.
- It’s the fallback value — CloudFront will use it as the TTL in such cases.

---

### 🧠 Example:

Let’s say you have:

- **Default TTL** = 86400 (1 day)
- **Min TTL** = 60 (1 min)
- **Max TTL** = 31536000 (1 year)

Now:

- If origin says `Cache-Control: max-age=3600`, CloudFront caches for 1 hour ✅
- If origin sends **no cache headers**, CloudFront caches for **1 day** (Default TTL)
- If origin says `max-age=10`, CloudFront caches for **60 sec** (Minimum TTL overrides it)
- If origin says `max-age=999999999`, CloudFront limits it to **1 year** (Maximum TTL)




---

# what are invalidations?

- So, incase you want to change an object, but then the cache in edge location will not be updated immediately, but you want to reflect the changes in one go, so you can go to the options of cloudfront, select the invadiation section and invalidate an object that you want to replace, or select the whooe bucket (in case of S3 origin), in which case the whole S3 origin cache would be donne again, immediately.


![[Screenshot from 2025-04-09 11-26-01.png]]
- there are the pattern matching exasmples

Now, one other way to make sure your changes gets reflected immediately, is to use versioned file naming convention. By using this ad also updating your html file, its gets reflectied immediately **Withnout the need to use invalidations!!** 

- Important- versioned naming convention is different from bucket versioning.
- infact, in bucket vwrsioning, the names of the file remain same.



How does versioned filenames work?

## What is "versioned file naming"?

It means adding a **version number** (or timestamp, hash, etc.) to your **file names** — like:

|Original|Versioned|
|---|---|
|`main.js`|`main.v2.js` or `main.20250409.js`|
|`style.css`|`style.abc123.css` (hash version)|

Why? Because **CloudFront sees different file names as entirely new files**, so it doesn’t serve the old cached version.

- so when we request for a cache, and it sees its not matching the content in the S3 origin, it modifies




so if there is a new object in my bucket, the cloudfront will make a new request?

###### ChatGPT said:

Yes! ✅ If the object is **new (i.e., has a new file name or path that CloudFront hasn’t seen before)**, then:

> **CloudFront will make a fresh request to your S3 origin the first time it’s accessed**, cache that object at the edge location, and serve it from cache for subsequent requests.




**You would jsut need to change the index.html file.**



How does invalidation looks like?

![[Screenshot from 2025-04-09 13-17-09.png]]


- bigger invalidation less frequently
- smaller invalidations more frequently
- youre billed based on invalidations


## Bigger Invalidation (Less Frequently) vs Smaller (More Frequently)

Here’s what this means:

|Strategy|Description|Cost Impact|Performance|
|---|---|---|---|
|**Bigger Invalidation, Less Frequently**|Invalidate using wildcards (e.g., `/static/*`) in one go|✅ Fewer requests → potentially **less costly**|❌ Invalidates more than needed|
|**Smaller Invalidations, More Frequently**|Invalidate individual files often (e.g., `/main.js`, `/index.html`)|❌ More paths = higher cost (if over free tier)|✅ Precise control over what’s invalidated|
- questions: if i change something in the html file and then make it available in the bucket, what will the cloudfront show? also, what if i did versioning to an image and then changed it in the html file? will the cloudfront do necessary changes? or do i have to use invalidations again?

