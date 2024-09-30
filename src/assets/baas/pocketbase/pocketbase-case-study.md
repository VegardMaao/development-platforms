---
title: Pocketbase
author: Vegard Maaø <VegardMaao>
tags: pocketbase, baas, SQLite, GO, sdk, js, open-spource, free, self-hosting
---

## Introduction

[Pocketbase](https://pocketbase.io/) is an open source BaaS Project, which can be seen as Supabase's little cousin.

Note that Pocketbase is still in development at the time of writing (September 2024), and backward compatibility is not something the developers can promise before the project reaches v1.0.0. This means it is not recommended for critical applications, unless you are willing to migrate to newer versions as the project comes along.

## Brief History:

## Features:

Pocketbase is a BaaS Provider with a SQLite embedded database, realtime subsctiptions, built-in auth management, conveinient dashboard UI and simple API which handles CRUD-actions (Create, Read, Update, and Delete).

It is built on Go, and can be extended using Go or JavaScript depending on your preference.

### Database:

Pocketbase is a powerful tool when setting up a relational database, with a quick and neat setup. PB uses SQLite under the hood to present you with **Collections**, which contain rows of data items. For instance, a "users" collection can contain rows of user objects with login credentials, post history, and more. And a "posts" collection can include post IDs, post names, post content, etc.

#### Collections:

**Collections** can handle all sorts of data types and fields, including, but not limited to; Text, email, booleans, numbers, dates, urls, and more.

You can administer your collections directly via the Admin page, and there are three types of collections.

**Base Collection** is the default collection type, and it can be used to store any application data (blog posts, products, etc.). Any data item in a base collection will always be assigned three base properties automatically; _id, created, updated_. Only the ID can be set manually if you want to, and must be a 15-character string.

**View Collection** is a read-only collection where data is produced from a plain SQL select statement. This means that users can use custom queries, which can provide powerful and custom results. With Custom SQL, you can extract, filter, join, union and alias data according to your needs.

A simple example would be SQL aggregation, where you collect a set of values, to return a single value. For instance, if you want to know the number of comments on blog posts in order to measure user engagement and analyze what your users enjoy.

**Auth Collections** will have all the features of a base collection, as well as handy fields that assist you in managing users and user authentication. Every Auth collection will have the following fields; _id, created, updated, username, email, emailVisibility, verified_.

There is no limit to how many Auth collections you can have, meaning that you can use them to manage users, admins and more in separate Auth collections, and each of these can have their own separate sets of fields and login credentials (like just email + password, or OAuth2).

#### Authentication:
