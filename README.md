[![Actions](https://github.com/emako/BuildTimestampGenerator/actions/workflows/dotnet.yaml/badge.svg)](https://github.com/emako/BuildTimestampGenerator/actions/workflows/dotnet.yml) [![nuget](https://img.shields.io/nuget/v/BuildTimestampGenerator)](https://www.nuget.org/packages/BuildTimestampGenerator) [![license: 0BSD](https://img.shields.io/badge/license-0BSD-green)](./LICENSE)

# 🛠⏲ BuildTimestampGenerator
Have you wanted a way to reliably get the time your application was compiled at, but still wanted to have 'deterministic' builds enabled? Well then do I have the package for you!

This is a small Roslyn source generator that outputs a class, `BuildTimestamp`, that contains several variables that describe when the source generator was run (and thus when your project was built.)

## ❓Usage

- Reference the source generator (sometimes called 'analyzer') in your `.csproj`, to [install it from NuGet](https://www.nuget.org/packages/BuildTimestampGenerator):
```xml
<ItemGroup>
	<PackageReference Include="BuildTimestampGenerator" Version="*" PrivateAssets="all" />
</ItemGroup>
```
  - If you want to refrence the project on disk rather than the NuGet package,
         see an example reference [here](https://docs.microsoft.com/en-us/dotnet/csharp/roslyn-sdk/source-generators-overview#code-try-4).
- Build once so packages are restored and source can be generated.
- Use the properties of the class `BuildTimestamp` to determine your compile time!

### ❗Example

#### 📥Source

```csharp
using System;

internal class Program
{
    private static void Main()
    {
        Console.WriteLine($"I was built at {BuildTimestamp.BuildTime}");
    }
}
```

#### 📤Output

```
I was built at 1/27/2022 12:54:21 PM
```

## 📝 License
BuildTimestampGenerator is [licensed](./LICENSE) under the Zero-Clause BSD License (SPDX-License-Identifier: 0BSD). If you're interested in cmdwtf.BuildTimestampGenerator under other terms, please contact the authors. cmdwtf.BuildTimestampGenerator may make use of several open source packages. Those packages are each covered by their own copyrights and licenses, which are available via the tooling you use to restore the packages when building. As well, some portions of code are distributed under terms of other licenses, which are designated in comments. See `LICENSE` for more details.

