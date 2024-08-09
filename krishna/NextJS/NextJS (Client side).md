
# Step 1 - NextJS Intro, Pre-requisites

### Pre-requisites

You need to understand basic Frontend before proceeding to this track.

You need to know what `React` is and how you can create a simple application in it

### NextJS Intro

NextJS was a framework that was introduced because of some `minor inconviniences` in React

1. In a React project, you have to maintain a separate Backend project for your API routes

2. React does not provide out of the box routing (you have to use react-router-dom)

3. React is not SEO Optimised

1. not exactly true today because of React Server components
2. we’ll discuss soon why

4. Waterfalling problem


# Step 2 - SEO Optimisation

Google/Bing has a bunch of `crawlers` that hit websites and figure out what the website does.

It ranks it on `Google` based on the HTML it gets back

The crawlers `DONT` usually run your JS and render your page to see the final output.

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fe7961f82-9447-4df5-a4e0-ce73dad86ffa%2FScreenshot_2024-03-02_at_10.06.37_AM.png?table=block&id=f018e860-6c2d-4435-91ec-b7e2727313b3&cache=v2)

💡

While Googlebot can run JavaScript, `dynamically generated` content is harder for the scraper to index

#### Try visiting a react website

What does the `Googlebot` get back when they visit a website written in react?

Try visiting [https://blog-six-tan-47.vercel.app/signup](https://blog-six-tan-47.vercel.app/signup)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F08ec429f-27b6-4518-8b4b-7c84d00151a8%2FScreenshot_2024-03-02_at_10.10.10_AM.png?table=block&id=a5c7d6ff-b0b5-4551-8cee-996f13715004&cache=v2)

Googlebot has no idea on what the project is. It only sees `Vite + React + TS` in the original HTML response.

Ofcourse when the JS file loads eventually, things get rendered but the `Googlebot` doesn’t discover this content very well.
# Step 3 - Waterfalling problem

Let’s say you built a blogging website in react, what steps do you think the `request cycle` takes?

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F58e004c5-0d4e-44f6-9a3b-7042ae5b979a%2FScreenshot_2024-03-02_at_10.42.47_AM.png?table=block&id=4848f05f-bf56-489c-8cbd-567b18af65dc&cache=v2)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F63cda89d-8385-4dd8-932a-4c5c474e9220%2FScreenshot_2024-03-02_at_11.25.40_AM.png?table=block&id=660dd700-22c4-42d8-bd63-18ae70aa3b1a&cache=v2)

1. Fetching the index.html from the CDN

2. Fetching script.js from CDN

3. Checking if user is logged in (if not, redirect them to /login page)

4. Fetching the actual blogs

There are 4 round trips that happen one after the other (sequentially)

💡

The "waterfalling problem" in React, and more broadly in web development, refers to a scenario where data fetching operations are chained or dependent on each other in a way that leads to inefficient loading behavior.

#### What does nextjs provide you?

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F06ef92dd-6676-4b50-bd2c-3f24e5537191%2FScreenshot_2024-03-02_at_11.55.58_AM.png?table=block&id=489dbf7b-618a-46e7-892d-54bc6d9fca73&cache=v2)


# Step 4 - Next.js offerings

Next.js provides you the following `upsides` over React

1. Server side rendering - Get’s rid of SEO problems

2. API routes - Single codebase with frontend and backend

3. File based routing (no need for react-router-dom)

4. Bundle size optimisations, Static site generation

5. Maintained by the Vercel team

Downsides -

1. Can’t be distributed via a CDN, always needs a server running that does `server side rendering` and hence is expensive

2. Very opinionated, very hard to move out of it
3. # Step 5 - Let’s bootstrap a simple Next app

```javascript
npx create-next-app@latest
```

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fd6a3439f-9ff8-456f-90bc-17501c0d46ba%2FScreenshot_2024-03-02_at_1.16.31_PM.png?table=block&id=5d438a5b-1c70-44a2-a409-aad9e9fa8009&cache=v2)

# File structure

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fbf0c63a2-c1e0-488d-82bb-8032ce792faa%2FScreenshot_2024-03-02_at_1.23.58_PM.png?table=block&id=8f7b4e4a-0360-4d4d-9079-fc6e66ff42a2&cache=v2)

1. next.config.mjs - Nextjs configuration file

2. tailwind.config.js - Tailwind configuration file

3. app - Contains all your code/components/layouts/routes/apis

#### Bootstrap the project

1. Remove everything from `app/page.tsx` and return an empty div

2. Remove the css bits (not the tailwind headers) from the `global.cs`
# Step 6 - Understanding routing in Next

### Routing in React

[https://blog-six-tan-47.vercel.app/signup](https://blog-six-tan-47.vercel.app/signup)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fc8f2b98f-bea9-48d8-842d-b08c53b4e247%2FScreenshot_2024-03-02_at_1.37.50_PM.png?table=block&id=29d75677-986c-4442-8e10-6d9e625d5e45&cache=v2)

### Routing in Next.js

Next.js has a `file based router` ([https://nextjs.org/docs/app/building-your-application/routing/defining-routes](https://nextjs.org/docs/app/building-your-application/routing/defining-routes))

This means that the way you create your files, describes what renders on a route

1. Let’s add a new folder in `app` called `signup`

2. Let’s add a file called `page.tsx` inside `app/signup`

page.tsx

1. Start the application locally

```javascript
npm run dev
```

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F879c5fdc-0044-4565-9f3b-342c22a9dec6%2FScreenshot_2024-03-02_at_1.49.52_PM.png?table=block&id=51800b16-8f20-472e-9b76-a68412aaa021&cache=v2)

#### Final folder structure

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F2cb8d576-6ac2-48e5-92e5-6b6056c3fe5e%2FScreenshot_2024-03-02_at_1.51.48_PM.png?table=block&id=928c7092-5eb6-4628-b689-7bc18f355d12&cache=v2)

#### Assignment - Can you add a `signin` route?

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F517e81a1-f286-4009-b2c0-27860fa0aa25%2FScreenshot_2024-03-02_at_1.54.58_PM.png?table=block&id=44aa8294-6c62-4639-9fe1-cfe8d9fe4d01&cache=v2)


# Step 7 - Prettify the signin page

Let’s replace the signup page with a prettier one

```javascript
export default function Signin() {
    return <div className="h-screen flex justify-center flex-col">
        <div className="flex justify-center">
        <a href="#" className="block max-w-sm p-6 bg-white border border-gray-200 rounded-lg shadow hover:bg-gray-100 ">
                <div>
                    <div className="px-10">
                        <div className="text-3xl font-extrabold">
                            Sign in
                        </div>
                    </div>
                    <div className="pt-2">
                        <LabelledInput label="Username" placeholder="harkirat@gmail.com" />
                        <LabelledInput label="Password" type={"password"} placeholder="123456" />
                        <button type="button" className="mt-8 w-full text-white bg-gray-800 focus:ring-4 focus:ring-gray-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2">Sign in</button>
                    </div>
                </div>
            </a>
        </div>
    </div>
}

interface LabelledInputType {
    label: string;
    placeholder: string;
    type?: string;
}

function LabelledInput({ label, placeholder, type }: LabelledInputType) {
    return <div>
        <label className="block mb-2 text-sm text-black font-semibold pt-4">{label}</label>
        <input type={type || "text"} id="first_name" className="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5" placeholder={placeholder} required />
    </div>
}
```

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fe3c99f5c-1a6c-47c0-b480-784333727cbc%2FScreenshot_2024-03-02_at_3.57.01_PM.png?table=block&id=efd1dff0-ee3e-4cd6-8a41-79955ad18d29&cache=v2)


# Step 8 - Server side rendering

Let’s try exploring the response from the server on the `/signup` route

1. Run `npm run dev`

2. Visit `http://localhost:3000/signup`

3. Notice the response you get back in your HTML file

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F0ee0691d-fbc6-4497-b603-4898d37787a8%2FScreenshot_2024-03-02_at_2.09.15_PM.png?table=block&id=85e54677-4daa-4370-9c19-27d604bfc1c0&cache=v2)

Now if `GoogleBot` tries to scrape your page, it’ll understand that this is a `signup page` without running any Javascript.

The first `index.html` file it get’s back will have context about the page since it was `server side rendered`

# Step 9 - Layouts

You’ll notice a file in your `app` folder called `layout.tsx`

Let’s see what this does (Ref [https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts))

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fcd19f926-6298-46f3-9dcb-8c56907b1b37%2FScreenshot_2024-03-02_at_2.23.58_PM.png?table=block&id=047751b2-37ae-41eb-a9bb-de63dd240cec&cache=v2)

#### What are layouts

Layouts let you `wrap` all child `pages` inside some logic.

#### Let’s explore layout.tsx

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F33811702-7311-4d7f-9f6d-ef39ff6da125%2FScreenshot_2024-03-02_at_3.12.40_PM.png?table=block&id=03bcbf0a-cb01-4b6d-8178-33edacc12efc&cache=v2)

### Assignment

Try adding a simple `Appbar`

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F88da4f72-9c11-4eec-a624-f9f7139cea31%2FScreenshot_2024-03-02_at_3.20.21_PM.png?table=block&id=379374e2-b0fb-4c49-86a3-6754ebc67948&cache=v2)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F5986a725-43fe-4b04-b993-a4fb7ccdc0e6%2FScreenshot_2024-03-02_at_3.21.08_PM.png?table=block&id=a118e5ae-addd-4dda-93cf-4daf1bab6a38&cache=v2)
# Step 10 - Layouts in sub routes

What if you wan’t all routes that start with `/signin` to have a `banner` that says `Login now to get 20% off`

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F304efd02-9d69-4b1a-95c5-f3d8bac5effb%2FScreenshot_2024-03-02_at_3.59.43_PM.png?table=block&id=9b26408a-59f9-45c3-ad19-0c28629c75c8&cache=v2)


# Step 11 - Merging routes

What if you wan’t to get the banner in both `signup` and `signin`?

### Approach #1

Move both the `signin` and `signup` folder inside a `auth` folder where we have the layout

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F3e7282fb-5bd0-4fc2-8704-13c0ca86d0f3%2FScreenshot_2024-03-02_at_4.06.41_PM.png?table=block&id=9fc88ce3-c520-43a3-b431-f30f816dd7be&cache=v2)

You can access the routes at

`http://localhost:3000/auth/signup` and `http://localhost:3000/auth/signin`

---

### Approach #2

You can use create a new folder with `()` around the name.

This folder is `ignored` by the router.

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F3e7624ce-20e0-459d-bea7-ee3b0f5b23f3%2FScreenshot_2024-03-02_at_4.09.56_PM.png?table=block&id=21e84824-4181-465d-9b02-40d08d210663&cache=v2)

You can access the routes at

`http://localhost:3000/signup` and `http://localhost:3000/signin`

# Step 12 - `components` directory

You should put all your `components` in a `components` directory and use them in the `app routes` rather than shoving everything in the route handler

1. Create a new folder called `components` in the root of the project

2. Add a new component there called `Signin.tsx`

3. Move the signin logic there

4. Render the `Signin` component in `app/(auth)signin/page.tsx`

Solution

`components/Signin.tsx`

```javascript
export function Signin() {
    return <div className="h-screen flex justify-center flex-col">
        <div className="flex justify-center">
        <a href="#" className="block max-w-sm p-6 bg-white border border-gray-200 rounded-lg shadow hover:bg-gray-100 ">
                <div>
                    <div className="px-10">
                        <div className="text-3xl font-extrabold">
                            Sign in
                        </div>
                    </div>
                    <div className="pt-2">
                        <LabelledInput label="Username" placeholder="harkirat@gmail.com" />
                        <LabelledInput label="Password" type={"password"} placeholder="123456" />
                        <button type="button" className="mt-8 w-full text-white bg-gray-800 focus:ring-4 focus:ring-gray-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2">Sign in</button>
                    </div>
                </div>
            </a>
        </div>
    </div>
}

interface LabelledInputType {
    label: string;
    placeholder: string;
    type?: string;
}

function LabelledInput({ label, placeholder, type }: LabelledInputType) {
    return <div>
        <label className="block mb-2 text-sm text-black font-semibold pt-4">{label}</label>
        <input type={type || "text"} id="first_name" className="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5" placeholder={placeholder} required />
    </div>
}
```

`app/(auth)/Signin.tsx`

```javascript
import { Signin as SigninComponent } from "@/components/Signin";

export default function Signin() {
    return <SigninComponent />
}
```


# Step 13 - Add a button onclick handler

Now try adding a `onclick` handler to the `button` on the signin page

```javascript
<button onClick={() => {
    console.log("User clicked on signin")
}} type="button" className="mt-8 w-full text-white bg-gray-800 focus:ring-4 focus:ring-gray-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2">Sign in</button>
```

You will notice an error when you open the page

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F016ae0b6-9072-4af8-9f0a-44e76d9dbbd4%2FScreenshot_2024-03-02_at_4.36.15_PM.png?table=block&id=df07ff59-b135-4a90-8edd-7a8097cedca0&cache=v2)

What do you think is happening here? Let’s explore in the next slide
# Step 14 - Client and server components

Ref - [https://nextjs.org/learn/react-foundations/server-and-client-components](https://nextjs.org/learn/react-foundations/server-and-client-components)

NextJS expects you to identify all your components as either `client` or `server`

As the name suggests

1. Server components are rendered on the server

2. Client components are pushed to the client to be rendered

By default, all components are `server` components.

If you wan’t to mark a component as a `client` component, you need to add the following to the top of the component -

```javascript
"use client"
```

**When should you create** **`client components`** **?**

1. Whenever you get an error that tells you that you need to create a client component

2. Whenever you’re using something that the server doesn’t understand (useEffect, useState, onClick…)

**Rule of thumb is to defer the client as much as possible**

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fcfd5f7c3-15ef-410c-95c0-381a0bb2a17e%2FScreenshot_2024-03-02_at_4.29.13_PM.png?table=block&id=3b38e275-9cc3-4fa7-9be7-c3ce2a9da066&cache=v2)

### Assignment

Try updating `components/Signin.tsx` to make it a client component

You will notice that the error goes away

Some nice readings -

[https://github.com/vercel/next.js/discussions/43153](https://github.com/vercel/next.js/discussions/43153)
