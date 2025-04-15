### what are behaviours in Cloudforont?
![[Screenshot from 2025-04-09 11-14-13.png]]
- so inside your origin, you want to restrict access or maintain different accesses to different things, this can be done using cache behaviour.
- **Behaviors define how CloudFront responds to requests** for specific paths or file types. Each behavior maps a **path pattern** (like `/images/*` or `/api/*`) to a **set of rules** that tells CloudFront:
	- Which origin to forward the request to
	- Whether to cache the response
	- Whether to allow cookies or query strings
	- Whether to compress the response
	- Which HTTP methods are allowed
	- Whether to use HTTPS
	- And more...
- Default Behavior vs Additional Behaviors:
	- **Default behavior**: Applies to **all requests** unless another behavior matches the path.
	- **Additional behaviors**: Can be added to match specific paths (e.g., `/api/*` or `/static/*`).

Check out the practical pictures in: [[implementations]]