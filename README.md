# DomainDrivenArch
This basically gives a markdown on the domain driven approach

1. dotnet new -o sln "Sln Name" e.g BookKeeping 
2. -> cd .\source\repos\BookKeeping\
3. -> ls

``
    Directory: C:\Users\Ilife\source\repos\BookKeeping


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----          2/4/2023  12:07 AM            441 BookKeeping.sln
``

PS C:\Users\Ilife\source\repos\BookKeeping> dotnet new webapi -o BookKeeping.Api
The template "ASP.NET Core Web API" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Api\BookKeeping.Api.csproj...
  Determining projects to restore...
  Restored C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Api\BookKeeping.Api.csproj (in 229 ms).
Restore succeeded.


PS C:\Users\Ilife\source\repos\BookKeeping> dotnet new classlib -o BookKeeping.Contracts
The template "Class Library" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Contracts\BookKeeping.Contracts.csproj...
  Determining projects to restore...
  Restored C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Contracts\BookKeeping.Contracts.csproj (in 62 ms).
Restore succeeded.


PS C:\Users\Ilife\source\repos\BookKeeping> dotnet new classlib -o BookKeeping.Infrastructure
The template "Class Library" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Infrastructure\BookKeeping.Infrastructure.csproj...
  Determining projects to restore...
  Restored C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Infrastructure\BookKeeping.Infrastructure.csproj (in 62
  ms).
Restore succeeded.


PS C:\Users\Ilife\source\repos\BookKeeping> dotnet new classlib -o BookKeeping.Application
The template "Class Library" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Application\BookKeeping.Application.csproj...
  Determining projects to restore...
  Restored C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Application\BookKeeping.Application.csproj (in 62 ms).
Restore succeeded.


PS C:\Users\Ilife\source\repos\BookKeeping> dotnet new classlib -o BookKeeping.Domain
The template "Class Library" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Domain\BookKeeping.Domain.csproj...
  Determining projects to restore...
  Restored C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Domain\BookKeeping.Domain.csproj (in 63 ms).
Restore succeeded.


PS C:\Users\Ilife\source\repos\BookKeeping> ls


    Directory: C:\Users\Ilife\source\repos\BookKeeping


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----          2/4/2023  12:09 AM                BookKeeping.Api
d-----          2/4/2023  12:10 AM                BookKeeping.Application
d-----          2/4/2023  12:09 AM                BookKeeping.Contracts
d-----          2/4/2023  12:10 AM                BookKeeping.Domain
d-----          2/4/2023  12:10 AM                BookKeeping.Infrastructure
-a----          2/4/2023  12:07 AM            441 BookKeeping.sln


PS C:\Users\Ilife\source\repos\BookKeeping> dotnet build
MSBuild version 17.3.2+561848881 for .NET
  Determining projects to restore...
C:\Program Files\dotnet\sdk\6.0.402\NuGet.targets(132,5): warning : Unable to find a project to restore! [C:\Users\Ilif
e\source\repos\BookKeeping\BookKeeping.sln]

Build succeeded.

C:\Program Files\dotnet\sdk\6.0.402\NuGet.targets(132,5): warning : Unable to find a project to restore! [C:\Users\Ilif
e\source\repos\BookKeeping\BookKeeping.sln]
    1 Warning(s)
    0 Error(s)

Time Elapsed 00:00:00.17
PS C:\Users\Ilife\source\repos\BookKeeping> dotnet sln add (ls -r **\*.csproj)
Project `BookKeeping.Api\BookKeeping.Api.csproj` added to the solution.
Project `BookKeeping.Application\BookKeeping.Application.csproj` added to the solution.
Project `BookKeeping.Contracts\BookKeeping.Contracts.csproj` added to the solution.
Project `BookKeeping.Domain\BookKeeping.Domain.csproj` added to the solution.
Project `BookKeeping.Infrastructure\BookKeeping.Infrastructure.csproj` added to the solution.
PS C:\Users\Ilife\source\repos\BookKeeping> dotnet build
MSBuild version 17.3.2+561848881 for .NET
  Determining projects to restore...
  All projects are up-to-date for restore.
  BookKeeping.Infrastructure -> C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Infrastructure\bin\Debug\net6.0\Boo
  kKeeping.Infrastructure.dll
  BookKeeping.Domain -> C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Domain\bin\Debug\net6.0\BookKeeping.Domain.
  dll
  BookKeeping.Application -> C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Application\bin\Debug\net6.0\BookKeepi
  ng.Application.dll
  BookKeeping.Contracts -> C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Contracts\bin\Debug\net6.0\BookKeeping.C
  ontracts.dll
  BookKeeping.Api -> C:\Users\Ilife\source\repos\BookKeeping\BookKeeping.Api\bin\Debug\net6.0\BookKeeping.Api.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:04.47
PS C:\Users\Ilife\source\repos\BookKeeping> dotnet add .\BookKeeping.Api\ reference .\BookKeeping.Contracts\ .\BookKeeping.Application\
Reference `..\BookKeeping.Contracts\BookKeeping.Contracts.csproj` added to the project.
Reference `..\BookKeeping.Application\BookKeeping.Application.csproj` added to the project.
PS C:\Users\Ilife\source\repos\BookKeeping> dotnet add .\BookKeeping.Infrastructure\ reference .\BookKeeping.Application\
Reference `..\BookKeeping.Application\BookKeeping.Application.csproj` added to the project.
PS C:\Users\Ilife\source\repos\BookKeeping> dotnet add .\BookKeeping.Application\ reference .\BookKeeping.Domain\
Reference `..\BookKeeping.Domain\BookKeeping.Domain.csproj` added to the project.
PS C:\Users\Ilife\source\repos\BookKeeping> dotnet add .\BookKeeping.Api\ reference .\BookKeeping.Infrastructure\
Reference `..\BookKeeping.Infrastructure\BookKeeping.Infrastructure.csproj` added to the project.
PS C:\Users\Ilife\source\repos\BookKeeping> code .
