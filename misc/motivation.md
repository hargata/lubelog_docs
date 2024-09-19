# Motivation

## Why LubeLogger is Created

Because frankly, it is outrageous that the options were between a glovebox full of receipts, a homemade spreadsheet, or cloud-dependent apps designed to gouge its users.

### We Understand Our Users

In the vein of Howard Beale from Network(1976), we at Hargata Softworks are mad as hell. We, as lifelong owners of rustbuckets and shitboxes, know the pain of vehicle maintenance all too well. We know the homemade spreadsheets are absolute hell to use on mobile devices, we know the folder full of receipts are terrible to organize and analyze, and most importantly, we know that when our users find a good, reliable software to track their vehicle maintenance, they will stick to the same software for years if not decades and they will expect the software to perform similarly down the road whether it's five or twenty five years from now.

### Our Mission

We set out to create a high-quality self-hosted alternative to all existing options in the market, and while it's not quite mission-accomplished, LubeLogger is gaining traction by the day and are reaching users all across the world.

The following chart shows where LubeLogger has positioned itself:

|      | SaaS | Self-Hosted |
| ---- | ---- | ----------- |
|  User-Friendly    | Existing apps in the market     | LubeLogger            |
| Non User-Friendly | Google Sheets | Box of receipts, Excel Spreadsheet        |

## Why Self-Hosted

### Pitfalls of "The Cloud"

We live in an interesting time where users have virtually zero ownership of their data. Software as a Service(SaaS) models can be beneficial for a lot of users and app developers, but it certainly takes away certain freedoms from the user. There is absolutely zero reason for an app which primary purpose is to store and manage personal data to be served exclusively via a SaaS model. Keep in mind that we here at LubeLogger are not against cloud applications, but when the only offerings in the market are delivered solely via the cloud, it opens up a lot of questions regarding how the user's data is being used especially in free-tier offerings. e.g.: If you're only using an app to store and analyze data for your 2014 Honda Accord, why is the only option to store your data in a server halfway across the world managed by an individual or corporate entity that may or may not be a going concern?

Being heavily reliant on "the cloud" for data storage and processing creates a lot of what-ifs scenarios that can lead to data-compromise and data-loss. What if the company/individual behind the app is no longer able to financially support the costs of the data storage or the development effort of the app? What will happen to the users' data then? And wouldn't that be extremely unfair towards the group of users that have paid for the app? Even if financial constraints were a non-issue, most apps in the market are still dependent on archaic protocols to "the cloud" that are subject to obsolescence and scalability issues.

The following reviews are of a competing app that have recently went through what we in the tech industry termed "Enshittification" that examplifies everything that can go wrong with being heavily reliant on "the cloud"

![](/Misc/Motivation/a/image-1726779500975.png)

![](/Misc/Motivation/a/image-1726779506523.png)

![](/Misc/Motivation/a/image-1726779517524.png)

While it may appear that there are numerous competent alternatives to this specific app in the market, there are absolutely no guarantees that those apps will be able to maintain their scalability in the future especially when their user count grows exponentially.

### Smaller Focus = Higher Quality Software

We're not some big corporation with staffs of engineers and sysadmins. Hargata Softworks is just me, my partner, and our cat, Frank. LubeLogger being self-hosted allows us to focus on delivering great software without having to split our attention across multiple domains such as server management, tech support, DDOS attacks, etc. Thanks to containerization and guides written by numerous individuals, LubeLogger is basically guaranteed to run on the majority of servers out there. We don't have to worry about running out of storage space or if our servers went down at 2am, because those responsibilities lie solely upon the user. This means that we get to dedicate our focus solely on developing and delivering new features to our users.

## Why Open-Source

### The Public is the Contingency Plan

As stated above, we aren't a huge corporation with staffs of engineers that can maintain this project perpetually. Since we have full-time jobs on top of this, the amount of dev time and effort we can invest in LubeLogger is dependent on how much free time / energy we have left after our employment obligations. Making it open source allows people to freely fork, contribute, and improve the app as they please.

### Revenue Generation

LubeLogger does not yet pay the bills, we are entirely dependent on donations to fund our development effort. Please see [[Funding|Misc/Funding]] on how to contribute.
