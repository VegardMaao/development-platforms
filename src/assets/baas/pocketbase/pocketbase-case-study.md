---
title: Pocketbase
author: Vegard Maaø <VegardMaao>
tags: pocketbase, baas, SQLite, GO, sdk, js, open-spource, free, self-hosting
---

## Introduction

[Pocketbase](https://pocketbase.io/) is an open source BaaS Project, which can be seen as Supabases little cousin.

Note that Pocketbase is still in development at the time of writing (September 2024), and backward compatibility is not something the developers can promise before the project reaches v1.0.0. This means it is not recommended for critical applications, unless you are willing to migrate to newer versions as the project comes along.

Pocketbase is a BaaS Provider with a SQLite embedded database, realtime subscriptions, built-in auth management, convenient dashboard UI and simple API which handles CRUD-actions (Create, Read, Update, and Delete).

It is built on Go, and can be extended using Go or JavaScript depending on your preference.

## History:

Because PocketBase is a relatively new project, digging up its history proved harder than expected. PocketBase started gaining traction in 2022, and the first public commit on GitHub was made the 6th of July 2022.

## Database:

Pocketbase is a powerful tool when setting up a relational database, with a quick and neat setup. PB uses SQLite under the hood to present you with **Collections**, which contain rows of data items. For instance, a "users" collection can contain rows of user objects with login credentials, post history, and more. And a "posts" collection can include post IDs, post names, post content, etc.

**Collections** can handle all sorts of data types and fields, including, but not limited to; Text, email, booleans, numbers, dates, urls, and more.

You can administer your collections directly via the Admin page, and there are three types of collections.

**Base Collection** is the default collection type, and it can be used to store any application data (blog posts, products, etc.). Any data item in a base collection will always be assigned three base properties automatically; _id, created, updated_. Only the ID can be set manually if you want to, and must be a 15-character string.

**View Collection** is a read-only collection where data is produced from a plain SQL select statement. This means that users can use custom queries, which can provide powerful and custom results. With Custom SQL, you can extract, filter, join, union and alias data according to your needs.

A simple example would be SQL aggregation, where you collect a set of values, to return a single value. For instance, if you want to know the number of comments on blog posts in order to measure user engagement and analyze what your users enjoy.

**Auth Collections** will have all the features of a base collection, as well as handy fields that assist you in managing users and user authentication. Every Auth collection will have the following fields; _id, created, updated, username, email, emailVisibility, verified_.

There is no limit to how many Auth collections you can have, meaning that you can use them to manage users, admins and more in separate Auth collections, and each of these can have their own separate sets of fields and login credentials (like just email + password, or OAuth2).

## Authentication:

The PocketBase API utilizes Json Web Tokens (JWT) for authentication via the HTTP header:

> Authorization: TOKEN

There are also dedicated Software Development Kit (SDK) helpers for this, making it easier to use.

**Authenticate as Admin:**
You can authenticate as an admin using email and password, but you can also have added security with OAuth2. More on this later. Admins can access anything on the server, and do not have to follow API rules.

**Authenticate as User:**
You can also authenticate as a user with email and password, or have added security with OAuth2. Additionally, you can use the built-in "requestVerification" functionality and the user.verified property to ensure that users are who they say they are. This can be useful to keep malicious actors out of your application.

Users have to abide by API rules, and will only access what you allow them to.

**Oauth2 Integration:**
Note that before integrating OAuth2 to your application, you need to create an Oauth2 app with the provider you choose. Information about how to do this is found on the web, but for the sake of the example, you can find Google's solution here:
https://developers.google.com/identity/protocols/oauth2

Once this is set up, PocketBase can handle the heavy lifting for you as seen in the [Docs](https://pocketbase.io/docs/authentication/).

## Hosting:

PocketBase is self-hosting only, unlike Supabase. You can use hosting services like Linode or [Fly](https://fly.io/), meaning you can deploy your site for cheap and easily manage your backend yourself. I also recommend checking out [PocketHost](https://pockethost.io/) for hosting.

## Advantages of PocketBase:

PocketBase is a very powerful and lightweight tool which can power small to midsize applications. It is also free to use, and can be used for hobby projects as well as small professional sites.

Furthermore, it only produces a single executable file, making it simple to deploy. You can also extend the framework yourself using Go or JavaScript, making it easier to customize your project.

## Disadvantages

The biggest disadvantage of PocketBase is that it can only scale vertically, meaning that the only way to scale up your project is to have a more powerful server. Or to put it simply, bigger volumes of traffic requires a bigger computer. However, this is not the end of the world, as most applications are unlikely to grow beyond what can be handled with vertical scaling.

Another disadvantage is that PocketBase is entirely self-hosted, unlike Supabase which offers a 25 dollar per month hosting option. However, as mentioned above, this can be remedied by hosting using Linode, PocketHost.io or a similar service. You can even set up your own server if you like.

## Conclusion:

PocketBase offers a simple, cheap and convenient way to set up and configure your backend and hosting. It is ideal for small to medium size projects, and is handy for hobby-projects. I would not recommend it for business applications at this point, as backwards compatibility is not guaranteed.

But if your goal is to learn, have fun and make something exiting for cheap, PocketBase is an ideal BaaS provider.
