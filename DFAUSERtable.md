---
title: dfaUSERTableStructure
toc: false
sidebar: labs_sidebar
folder: master
permalink: /dfa_user_table_doc.html
summary: api docs
applies_to: [developer,administrator,consumer]
---

# Database Structure - DFAUSER
===============

## Document Sample (c) 2218 Cryocorp LLC

***WARNING - DO NOT USE WITHOUT PROPER AUTHORIZATION*** 

This document will provide the basic information on the DFAUSER table as part of the overal Cryocorp Chamber Management System (CCMS).

The DFAUser table contains the key users of the CCMS that might need API Access. 

Below is a column list:

`USERID` -> Internal User ID for this table - **NOTE** this differs from the `CCYUSID`

`FIRSTNAME` -> Self explanatory

`LASTNAME` -> Self Explanatory

`FULLNAME` -> Self Explanatory

`CCYUSID` -> In order to use the APIs,  use this value as the user id.

**NOTE** Acesss to this DB is restricted. Keep your passwords secure.