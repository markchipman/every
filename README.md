# Ever.y

Ever.y is a fluent API job scheduling engine for .NET.

Please feel free to issue PRs or suggest improvements or new features.

## Installation
Ever.y can be found on [NuGet](https://www.nuget.org/packages/Ever.y). Search for _Ever.y_ in the NuGet Package Manager, or use the Package Manager Console:

```
Install-Package Ever.y
```

## Examples

```c#
Ever.y().Second.Do(() => Console.WriteLine("Every second"));
Ever.y(2).Days.At(15).Do(() => Console.WriteLine("Every 2 days at 15:00"));
Ever.y(3).rd(Fri.day).OfTheMonth.At(16, 30).Do(() => Console.WriteLine("Every 3rd Friday of the month at 16:30"));
Ever.y().Day.At(12).Utc(-4).Do(() => Console.WriteLine("Every day at 12:00 in the UTC-04:00 time zone"));
Ever.y(21).stOfTheMonth.At(7, 45).Do(() => Console.WriteLine("Every 21st of the month at 7:45"));

Once.After(2).Seconds.Do(() => Console.WriteLine("Once, after 2 seconds"));
```

```c#
class MyClass { public string MyProp { get; set; } }
//...
Action<Job<MyClass>> job = (j) => Console.WriteLine($"My job has metadata: {j.Metadata.MyProp}");
var metadata = new MyClass { MyProp = "Hello World!" };

Ever.y(Thurs.day).At(4).Do(job, metadata); // Every Thursday at 04:00, do job
```

## Credits
Icon by [Freepik](http://www.flaticon.com/authors/freepik).
