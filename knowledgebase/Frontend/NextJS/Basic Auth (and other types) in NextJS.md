To handle auth in NextJS just put middleware.ts (in case of TypeScript) to root folder of the project (beside package.json) with content like present below:

```typescript
import { NextRequest, NextResponse } from 'next/server';  
  
const reBasicAuth = /^Basic\s+(\S+)$/;  
const users: Record<string, string> = {  
	'test': 'test'  
};  
  
export function middleware(req: NextRequest) {  
	const auth = req.headers.get('authorization');  
	if (!auth) {  
		return new NextResponse(null, {  
			status: 401,  
			headers: {  
				'WWW-Authenticate': 'Basic'  
			}  
		});  
	}  
	const basic = reBasicAuth.exec(auth);  
	if (basic) {  
		const [user, password] = atob(basic[1]).split(':');  
		const valid = users[user] === password;  
		if (valid) {  
			return NextResponse.next();  
		}  
	}  
	return new NextResponse(null, { status: 401 });  
}
```