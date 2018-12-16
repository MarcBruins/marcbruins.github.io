# C# 8 Nullable reference types updating guide

C# 8.0 will introduce a new groundbreaking feature called `Nullable reference types`, this feature will change the way we currently develop our software in C# by making, you guessed it, reference types nullable. 

This guide serves as a practical introduction to the problem and how you should solve those problems.

## Why should we use it?
There are multiple benefits in using this feature. The first and foremost is type safety for reference types. In the end it is very weird that we can assign a value to a reference type that is not of that type. For example: 

` C#
string helloNull = null; 
`

Will cause a compiler butt kick! Because `null` is not a string! 

The second benefit is that it will make the `intent` of your code very clear. It tells you and the users of your solution how your code should be used and handled. In the blink of an eye you'll see what this code should do, and if your are doing it wrong the compiler will give you a kick in the butt.

The whole ecosystem including all the libraries that we all use will eventually be safer to use because they generate no null reference error and the intent of the libraries is much more clear!

*If you are still not convinved that null is a bad idea, then the creator of the `billion dollar mistake` also know as `null` has [publicly apolizeged for introducing it](https://en.wikipedia.org/wiki/Tony_Hoare#Apologies_and_retractions).* 


## Enabling
As this is a breaking change we need to enable it. Add the following to your `csproj` or maybe even better to your `Directory.build.props`:

` XML

    <LangVersion>8</LangVersion>
    <TreatWarningsAsErrors>true</TreatWarningsAsErrors>
    <NullableReferenceTypes>true</NullableReferenceTypes>
`

Welcome to .NET Hardcore

![.NET Hardcore](../public/img/DotnetHardcode.PNG})


# Errors




