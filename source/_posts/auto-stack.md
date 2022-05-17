---
title: Auto Stack - Low Code Full Stack App Generator
date: 2022-02-08 19:47:35
tags: diy, code generation
---

# Auto Stack 

Auto Stack is tool aiming to generate a full stack application from existing templates and best practices. Users can also provide their own template for customization. 

The core of the system consists of database extractor and code generation engine. 

Work Flow:
- User create data model / extract data model from existing database such as MySQL, PostgreSQL or MongoDB
- Generating Backup API (CURD) from templates written in PHP, node.js, go. 
- Generating OpenAPI yaml file.
- Using OpenAPI Generator to generate client library of the backup code.
- Generating front end code in React / Vue / Flutter with user login and CURD table for each page.


