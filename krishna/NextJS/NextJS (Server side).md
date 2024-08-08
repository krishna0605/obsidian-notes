# Step 1 - Backends in Next.js

**Next.js is a full stack framework**

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F293901d8-52c1-468b-8da4-118a492cc4d5%2FScreenshot_2024-03-03_at_1.19.40_PM.png?table=block&id=3cc70195-060b-4a7c-a4fb-a4f5788cc473&cache=v2)

This means the same `process` can handle frontend and backend code.

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F0c3f1413-7ba1-4761-980c-64395b29c008%2FScreenshot_2024-03-03_at_1.22.57_PM.png?table=block&id=4f15fe71-93d7-44c0-9ded-a8c6a182161c&cache=v2)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F5d08223e-3073-480d-9bd0-cdfcf7e7f9ae%2FScreenshot_2024-03-03_at_1.22.29_PM.png?table=block&id=4d854a66-d41e-4973-a1b7-570d1543f936&cache=v2)

#### Why?

1. Single codebase for all your codebase

2. No cors issues, single domain name for your FE and BE

3. Ease of deployment, deploy a single codebase
# Step 2 - Recap of Data fetching in React

Let’s do a quick recap of how data fetching works in React

💡

We’re not building backend yet Assume you already have this backend route - [https://week-13-offline.kirattechnologies.workers.dev/api/v1/user/details](https://week-13-offline.kirattechnologies.workers.dev/api/v1/user/details)

Code - [https://github.com/100xdevs-cohort-2/week-14-2.1](https://github.com/100xdevs-cohort-2/week-14-2.1)

Website - [https://week-14-2-1.vercel.app/](https://week-14-2-1.vercel.app/)

### User card website

Build a website that let’s a user see their name and email from the given endpoint

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F04381271-2b80-445f-a355-79ecd2eb1475%2FScreenshot_2024-03-03_at_2.07.00_PM.png?table=block&id=77a11326-766b-495c-8d14-05403a3d3f5c&cache=v2)

### UserCard component

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Ff648616d-6b9e-4a1d-9432-8adb14d66680%2FScreenshot_2024-03-03_at_1.47.41_PM.png?table=block&id=b83be595-6a7c-4531-8313-1ab53db75612&cache=v2)

### Data fetching happens on the client

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F87c7dd9a-b6c8-4aa6-89b4-c0ff6e4c394d%2FScreenshot_2024-03-02_at_5.54.35_PM.png?table=block&id=79ec6fba-7aa8-457c-bfae-a4de19b2dc7c&cache=v2)

# Step 3 - Data fetching in Next

Ref - [https://nextjs.org/docs/app/building-your-application/data-fetching/fetching-caching-and-revalidating](https://nextjs.org/docs/app/building-your-application/data-fetching/fetching-caching-and-revalidating)

💡

You can do the same thing as the last slide in Next.js, but then you lose the benefits of `server side rendering`

You should fetch the user details on the server side and `pre-render` the page before returning it to the user.

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F9e649d49-1f77-4f15-a9c9-8988053fb978%2FScreenshot_2024-03-03_at_2.23.27_PM.png?table=block&id=0cc99c83-e71b-435f-b545-a1dbe0dd5070&cache=v2)

### Let’s try to build this

1. Initialise an empty next project

```javascript
 npx create-next-app@latest
```

1. Install axios

```javascript
npm i axios
```

1. Clean up `page.tsx`, `global.css`

2. In the root `page.tsx`, write a function to fetch the users details

```javascript
async function getUserDetails() {
  const response = await axios.get("https://week-13-offline.kirattechnologies.workers.dev/api/v1/user/details")
	return response.data;
}
```

1. Convert the default export to be an async function (yes, nextjs now supports `async` components)

```javascript
import axios from "axios";

async function getUserDetails() {
  const response = await axios.get("https://week-13-offline.kirattechnologies.workers.dev/api/v1/user/details")
	return response.data;
}

export default async function Home() {
  const userData = await getUserDetails();

  return (
    <div>
      {userData.email}
      {userData.name}
    </div>
  );
}
```

1. Check the network tab, make sure there is no waterfalling

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Ffadf2f02-7196-4ce1-8c69-9c2d8ab03b50%2FScreenshot_2024-03-03_at_2.32.47_PM.png?table=block&id=b8f2c8ae-501c-4c6c-ac5a-f489babd212e&cache=v2)

1. Prettify the UI

```javascript
import axios from "axios";

async function getUserDetails() {
  const response = await axios.get("https://week-13-offline.kirattechnologies.workers.dev/api/v1/user/details")
	return response.data;
}

export default async function Home() {
  const userData = await getUserDetails();

  return (
    <div className="flex flex-col justify-center h-screen">
        <div className="flex justify-center">
            <div className="border p-8 rounded">
                <div>
                    Name: {userData?.name}
                </div>
                
                {userData?.email}
            </div>
        </div>
    </div>
  );
}
```

Good question to ask at this point - Where is the `loader` ?

Do we even need a `loader` ?

# Step 4 - Loaders in Next

What if the `getUserDetails` call takes 5s to finish (lets say the backend is slow). You should show the user a `loader` during this time

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fedccd049-a0f2-461e-af42-2038ede9cc63%2FScreenshot_2024-03-03_at_2.42.02_PM.png?table=block&id=533d873c-63e0-4c1c-9f3b-f40980f1e696&cache=v2)

#### loading.tsx file

Just like `page.tsx` and `layout.tsx` , you can define a `skeleton.tsx` file that will render until all the async operations finish

1. Create a `loading.tsx` file in the root folder

2. Add a custom loader inside

```javascript
export default function Loading() {
    return <div className="flex flex-col justify-center h-screen">
        <div className="flex justify-center">
            Loading...
        </div>
    </div>
  }
```

# Step 5 - Introducing api routes in Next.js

NextJS lets you write backend routes, just like express does.

This is why Next is considered to be a `full stack` framework.

The benefits of using NextJS for backend includes -

1. Code in a single repo

2. All standard things you get in a backend framework like express

3. Server components can directly talk to the backend
# Step 6 - Let’s move the backend into our own app

We want to introduce a route that returns `hardcoded` values for a user’s details (email, name, id)

1. Introduce a new folder called `api`

2. Add a folder inside called `user`

3. Add a file inside called `route.ts`

4. Initialize a `GET` route inside it

```javascript
export async function GET() {
  return Response.json({ username: "harkirat", email: "harkirat@gmail.com" })
}
```

1. Try replacing the api call in `page.tsx` to hit this URL

```javascript
async function getUserDetails() {
  try {
    const response = await axios.get("http://localhost:3000/api/user")
	  return response.data;
  }  catch(e) {
    console.log(e);
  }
}
```

💡

This isn’t the best way to fetch data from the backend. We’ll make this better as time goes by

# Step 7 - Frontend for Signing up

1. Create `app/signup/page.tsx`

2. Create a simple Page

```javascript
import { Signup } from "@/components/Signup"

export default function() {
    return <Signup />
}
```

1. Create `components/Signup.tsx`

Code

```javascript
import axios from "axios";
import { ChangeEventHandler, useState } from "react";

export function Signup() {
    const [username, setUsername] = useState("");
    const [password, setPassword] = useState("");

    return <div className="h-screen flex justify-center flex-col">
        <div className="flex justify-center">
        <a href="#" className="block max-w-sm p-6 bg-white border border-gray-200 rounded-lg shadow hover:bg-gray-100 ">
                <div>
                    <div className="px-10">
                        <div className="text-3xl font-extrabold">
                            Sign up
                        </div>
                    </div>
                    <div className="pt-2">
                        <LabelledInput onChange={(e) => {
                            setUsername(e.target.value);
                        }} label="Username" placeholder="harkirat@gmail.com" />
                        <LabelledInput onChange={(e) => {
                            setPassword(e.target.value)
                        }} label="Password" type={"password"} placeholder="123456" />
                        <button type="button" className="mt-8 w-full text-white bg-gray-800 focus:ring-4 focus:ring-gray-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2">Sign in</button>
                    </div>
                </div>
            </a>
        </div>
    </div>

}

function LabelledInput({ label, placeholder, type, onChange }: LabelledInputType) {
    return <div>
        <label className="block mb-2 text-sm text-black font-semibold pt-4">{label}</label>
        <input onChange={onChange} type={type || "text"} id="first_name" className="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5" placeholder={placeholder} required />
    </div>
}

interface LabelledInputType {
    label: string;
    placeholder: string;
    type?: string;
    onChange: ChangeEventHandler<HTMLInputElement>
}
```

1. Convert `components/Signup.tsx` to a client component

```javascript
"use client"
```

1. Add a `onclick handler` that sends a `POST request` to `/user`

```javascript
 <button onClick={async () => {
    const response = await axios.post("http://localhost:3000/api/user", {
        username,
        password
    });
    
}} type="button" className="mt-8 w-full text-white bg-gray-800 focus:ring-4 focus:ring-gray-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2">Sign in</button>
```

1. Route the user to landing page if the signup succeeded Ref useRouter hook - [https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#userouter-hook](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#userouter-hook)

Final signup.tsx

```javascript
import axios from "axios";
import { useRouter } from "next/router";
import { ChangeEventHandler, useState } from "react";

export function Signup() {
    const [username, setUsername] = useState("");
    const [password, setPassword] = useState("");
    const router = useRouter();

    return <div className="h-screen flex justify-center flex-col">
        <div className="flex justify-center">
        <a href="#" className="block max-w-sm p-6 bg-white border border-gray-200 rounded-lg shadow hover:bg-gray-100 ">
                <div>
                    <div className="px-10">
                        <div className="text-3xl font-extrabold">
                            Sign up
                        </div>
                    </div>
                    <div className="pt-2">
                        <LabelledInput onChange={(e) => {
                            setUsername(e.target.value);
                        }} label="Username" placeholder="harkirat@gmail.com" />
                        <LabelledInput onChange={(e) => {
                            setPassword(e.target.value)
                        }} label="Password" type={"password"} placeholder="123456" />
                        <button onClick={async () => {
                            const response = await axios.post("http://localhost:3000/api/user", {
                                username,
                                password
                            });
                            router.push("/")
                        }} type="button" className="mt-8 w-full text-white bg-gray-800 focus:ring-4 focus:ring-gray-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2">Sign in</button>
                    </div>
                </div>
            </a>
        </div>
    </div>

}

function LabelledInput({ label, placeholder, type, onChange }: LabelledInputType) {
    return <div>
        <label className="block mb-2 text-sm text-black font-semibold pt-4">{label}</label>
        <input onChange={onChange} type={type || "text"} id="first_name" className="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5" placeholder={placeholder} required />
    </div>
}

interface LabelledInputType {
    label: string;
    placeholder: string;
    type?: string;
    onChange: ChangeEventHandler<HTMLInputElement>
}
```

💡

We still have to implement the backend route, lets do that in the next slide

# Step 8 - Backend for signing up

Add a `POST` route that takes the users email and password and for now just returns them back

1. Navigate to `app/api/user/route.ts`

2. Initialize a POST endpoint inside it

```javascript
import { NextRequest, NextResponse } from 'next/server';

export async function POST(req: NextRequest) {
    const body = await req.json();

    return NextResponse.json({ username: body.username, password: body.password })
}
```

Ref - [https://nextjs.org/docs/app/api-reference/functions/next-response](https://nextjs.org/docs/app/api-reference/functions/next-response)

# Step 9 - Databases!

We have a bunch of dummy routes, we need to add a database layer to persist data.

Adding prisma to a Next.js project is straightforward.

💡

Please get a free Postgres DB from either neon or aiven

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F0f88d21e-4369-4e14-a924-46d0cbfe5579%2FScreenshot_2024-03-03_at_3.51.39_PM.png?table=block&id=5934a2b8-79bd-4a6f-be78-4a4325cd4acd&cache=v2)

1. Install prisma

```javascript
npm install prisma
```

1. Initialize prisma schema

```javascript
npx prisma init
```

1. Create a simple user schema

```javascript
model User {
  id        Int     @id  @default(autoincrement())
  username  String  @unique
  password  String
}
```

1. Replace `.env` with your own Postgres URL

```javascript
DATABASE_URL="postgresql://johndoe:randompassword@localhost:5432/mydb?schema=public"
```

1. Migrate the database

```javascript
npx prisma migrate dev --name init_schema
```

1. Generate the client

```javascript
npx prisma generate
```

1. Finish the `signup` route

```javascript

export async function POST(req: NextRequest) {
    const body = await req.json();
    // should add zod validation here
    const user = await client.user.create({
        data: {
            username: body.username,
            password: body.password
        }
    });

    console.log(user.id);

    return NextResponse.json({ message: "Signed up" });
}
```

1. Update the `GET` endpoint

```javascript
export async function GET() {
    const user = await client.user.findFirst({});
    return Response.json({ name: user?.username, email: user?.username })
}
```

💡

We’re not doing any authentication yet. Which is why we’re not returning a jwt (or setting a cookie) here

# Step 10 - Better fetches

For the root page, we are fetching the details of the user by hitting an HTTP endpoint in `getUserDetails`

### Current solution

```javascript
import axios from "axios";

async function getUserDetails() {
  try {
    const response = await axios.get("http://localhost:3000/api/user")
	  return response.data;
  }  catch(e) {
    console.log(e);
  }
}

export default async function Home() {
  const userData = await getUserDetails();

  return (
    <div className="flex flex-col justify-center h-screen">
        <div className="flex justify-center">
            <div className="border p-8 rounded">
                <div>
                    Name: {userData?.name}
                </div>
                
                {userData?.email}
            </div>
        </div>
    </div>
  );
}
```

`getUserDetails` runs on the server. This means you’re sending a request from a server back to the server

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F71abac43-74f7-44a7-a974-b8202c7ed862%2FScreenshot_2024-03-03_at_5.09.36_PM.png?table=block&id=93cc8990-749e-4723-a1d6-487154c2f7e9&cache=v2)

### Better solution

```javascript
import { PrismaClient } from "@prisma/client";

const client = new PrismaClient();

async function getUserDetails() {
  try {
    const user = await client.user.findFirst({});
	  return {
      name: user?.username,
      email: user?.username
    }
  }  catch(e) {
    console.log(e);
  }
}

export default async function Home() {
  const userData = await getUserDetails();

  return (
    <div className="flex flex-col justify-center h-screen">
        <div className="flex justify-center">
            <div className="border p-8 rounded">
                <div>
                    Name: {userData?.name}
                </div>
                
                {userData?.email}
            </div>
        </div>
    </div>
  );
}
```

# Step 11 - Singleton prisma client

Ref - [https://www.prisma.io/docs/orm/more/help-and-troubleshooting/help-articles/nextjs-prisma-client-dev-practices](https://www.prisma.io/docs/orm/more/help-and-troubleshooting/help-articles/nextjs-prisma-client-dev-practices)

1. Create `db/index.ts`

2. Add a prisma client singleton inside it

```javascript
import { PrismaClient } from '@prisma/client'

const prismaClientSingleton = () => {
  return new PrismaClient()
}

declare global {
  var prisma: undefined | ReturnType<typeof prismaClientSingleton>
}

const prisma = globalThis.prisma ?? prismaClientSingleton()

export default prisma

if (process.env.NODE_ENV !== 'production') globalThis.prisma = prisma
```

1. Update imports of prisma everywhere

```javascript
import client from "@/db"
```

# Step 12 - Server Actions

Ref - [https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions-and-mutations](https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions-and-mutations)

Right now, we wrote an `API endpoint` that let’s the user sign up

```javascript
export async function POST(req: NextRequest) {
    const body = await req.json();
    // should add zod validation here
    const user = await client.user.create({
        data: {
            username: body.username,
            password: body.password
        }
    });

    console.log(user.id);

    return NextResponse.json({ message: "Signed up" });
}
```

What if you could do a simple function call (even on a `client component` that would run on the server?) (similar to `RPC` )

💡

Under the hood, still an HTTP request would go out. But you would feel like you’re making a function call

# Steps to follow

1. Create `actions/user.ts` file (you can create it in a different folder)

2. Write a function that takes `username` and `password` as input and stores it in the DB

```javascript
"use server"

import client from "@/db"

export async function signup(username: string, password: string) {
    // should add zod validation here
    const user = await client.user.create({
        data: {
            username: username,
            password: password
        }
    });

    console.log(user.id);

    return "Signed up!"
}
```

1. Update the `Signup.tsx` file to do the function call

```javascript
import { signup } from "@/actions/user";;

...

<button onClick={async () => {
    const response = await signup(username, password);
    localStorage.setItem("token", response);
    router.push("/")
}} type="button" className="mt-8 w-full text-white bg-gray-800 focus:ring-4 focus:ring-gray-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2">Sign in</button>
```

## Check the network tab

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F5c2df6c3-b672-49a6-bd49-bef3797e9c05%2FScreenshot_2024-03-03_at_6.03.43_PM.png?table=block&id=9e3a311b-c236-43fe-9eb5-21e199fa6498&cache=v2)

### Benefits of server actions

1. Single function can be used in both client and server components

2. Gives you types of the function response on the frontend (very similar to trpc)

3. Can be integrated seamlessly with forms (ref [https://www.youtube.com/watch?v=dDpZfOQBMaU](https://www.youtube.com/watch?v=dDpZfOQBMaU))