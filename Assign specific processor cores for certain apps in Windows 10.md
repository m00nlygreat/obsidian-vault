![](https://cdn.mos.cms.futurecdn.net/vZr8VQjjgACFcrR7rgjPxX-320-80.jpg)

  

For the last few weeks, Windows Central has been documenting and explaining various tips for [Windows 10](https://www.windowscentral.com/software-apps/windows-10) meant for novices and those new to Windows. Today, we are taking a look at a more advanced tip that some enthusiasts may like. Once again, this is a carry-over from previous iterations of Windows so it is not new, but like ['God Mode'](https://www.windowscentral.com/how-enable-god-mode-windows-10) many people may not know about it or have simply forgotten the feature.

In Windows 10 and under an administrative account you can specify which cores (of your presumably multi-core processor) gets used for explicit apps.

Why would you want to do this setting? In this regard, it is only for the power user as most consumer-level users either won't reap the benefits or may even make things worse. The longer explanation is assigning specific cores to an app can, in some cases, improve overall system effectiveness. For instance, if you are doing some heavy rendering, compiling, or video work, this ensures that part of the processor is always dedicated to the task.

Looking at [Wikipedia](https://en.wikipedia.org/wiki/Processor_affinity), this is what they say on the matter for those more technically inclined:

RECOMMENDED VIDEOS FOR YOU...

Windows Central

> "Processor affinity takes advantage of the fact that some remnants of a process that was run on a given processor may remain in that processor's memory state (for example, data in the CPU cache) after another process is run on that CPU. Scheduling that process to execute on the same processor could result in an efficient use of process by reducing performance-degrading situations such as cache misses. A practical example of processor affinity is executing multiple instances of a non-threaded application, such as some graphics-rendering software."

Mind you, Windows, and by extension Windows 10, is actually very good at managing your processor cores and allocating resources where it is needed. However, this is Windows, so you are the master and you can override things when you want.

**Your best bet:** _Proceed with caution and take notes on what you change so you can easily revert if things get wonky._

## How to designate cores to a particular app

## 1\. Make sure you are using the Administrator account or have Admin privileges

## 2\. Right click on the Task Bar and choose Task Manager (or type in Task Manager in the search bar)

![](https://cdn.mos.cms.futurecdn.net/mvuL8WJPWx7mCfjNyurV5E.png)

## 3\. Once Task Manager is launched choose More Details near the bottom

![](https://cdn.mos.cms.futurecdn.net/FrKbwC5WwFTKavaexzhgcL.png)

## 4\. Choose the app (that is already running) that you would like to designate cores for

![](https://cdn.mos.cms.futurecdn.net/VJbXDW8dHFvFrGehm8ieAh.png)

## 5\. Right-click on the app and select Go to details

![](https://cdn.mos.cms.futurecdn.net/mXbhDTpHEe5yuD85ykzihb.png)

## 6\. Under details again right-click on the app and now choose Set Affinity

![](https://cdn.mos.cms.futurecdn.net/zCeE2vNXGonRzaavmN2y3U.png)

## 7\. In the Processor Affinity windows uncheck the CPU cores but leave the ones you want to set core affinity for

![](https://cdn.mos.cms.futurecdn.net/YzPHx5gEPVqWnGxXqjvLcg.png)

## 8\. Once done, click OK to save the settings

![](https://cdn.mos.cms.futurecdn.net/2f7E8wiSQQYJExgdjCp9yB.png)

## 10\. Restarting the computer will revert the changes

## Wrap up

Overall, this is a simple change that is very easy to implement. The real question is, _Do you need to do it?_

If you are considering this modification, you likely know why you want to do it. However, for regular users you likely won't get much value.

**Do you have specific instances where setting core affinity for specific apps is beneficial? How do you use this setup and for which apps?** Share with us your experience in comments!

_If you think this guide is helpful, we have many more posts like this in our Windows 10 help, tips, and tricks page. Or try our massive [Windows 10 Forums at Windows Central](https://forums.windowscentral.com/#windows-10-hub) for more help!_

_Thanks, @Nabkawe5, for the tip!_

All the latest news, reviews, and guides for Windows and Xbox diehards.

Daniel Rubino is the Editor-in-chief of Windows Central, head reviewer, [podcast](https://www.windowscentral.com/tag/podcasts) co-host, and analyst. He has been covering Microsoft since 2007 when this site was called WMExperts (and later Windows Phone Central). His interests include Windows, laptops, next-gen computing, and for some reason, watches. Before all this tech stuff, he worked on a Ph.D. in linguistics, watched people sleep (for medical purposes!), and ran the projectors at movie theaters because it was fun.