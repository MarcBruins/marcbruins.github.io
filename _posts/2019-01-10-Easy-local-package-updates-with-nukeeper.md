---
layout: post
title: Easy local package updates with NuKeeper update
---

Ever get tired of updating `nuget` packages all over the place? I know i was. For a project that i'm currently working on we have a microservices architecture with about four domains. We have our own packages distributed by `azure devops` that are used in all of these domains. The packages are `EventSourcing.Shared`, `EventSourcing.Store`, `EventSourcing.PubSub` and a few more.

Now every time we update the sourcecode of EventSourcing. We are required to open all different solution and update all the packages to the latest version. This is a very tedious and boring task. Fortunately there is a tool out there that can help us do this, hello `NuKeeper`!

<!--more-->

# NuKeeper
[NuKeeper](https://github.com/NuKeeperDotNet/NuKeeper) is a *dotnet tool* that automagically update NuGet packages in all your .NET projects. It is not tied to a specific solution or project file, you can target you current directory and it will work for all your `csproj` or even your `Directory.Build.props` file. 

It has some very powerful commands that you can check out on the [website](https://github.com/NuKeeperDotNet/NuKeeper#commands). I might blog about them later on but for now let's focus on our problem!

<em><small>
Installing it is a simple as `dotnet tool install nukeeper --global`
</small></em>

# Solution
As you can see on the NuKeeper website there is a command called `update`. It will update all your Nuget Packages that you target on your *local file system*. It also has a really nice feature in which you can provide a `regex` pattern so that we can specify only the packages that we want updated! So to update our local packages the only thing we have to do is:

`nukeeper update --include ^EventSourcing. --age 0 --maxupdate 50`

* `--include` takes a regex on which packages we want to update
* `--age` allows you to specify the age of your packages, for our use case we just updated the `eventsourcing` source so we want the latest and greatest bits. Default is 7 days.
* `--maxupdate` the name already says it, how many update do you want to do at max?

That's it! No more opening `.sln` everywhere and opening your `package manager` screen to update it all. Just run the command and you are done!

<em><small>
Want to automatically update and create a PR? Have a look at the `repo` command. This will create PR's on your repo!
</small></em>

