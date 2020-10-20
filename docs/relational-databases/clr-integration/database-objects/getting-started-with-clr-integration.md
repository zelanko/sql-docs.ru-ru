---
title: начало работы с интеграцией со средой CLR | Документация Майкрософт
description: В этой статье описываются пространства имен и библиотеки, необходимые для компиляции объектов базы данных с помощью интеграции Microsoft SQL Server с .NET Framework CLR.
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: quickstart
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration]
- namespaces [CLR integration]
- database objects [CLR integration], about CLR integration
- stored procedures [CLR integration]
- common language runtime [SQL Server], about CLR integration
- building database objects [CLR integration], about CLR integration
- common language runtime [SQL Server], stored procedures
- common language runtime [SQL Server], namespaces
- Hello World example [CLR integration]
- library [CLR integration]
ms.assetid: c73e628a-f54a-411a-bfe3-6dae519316cc
author: rothja
ms.author: jroth
ms.openlocfilehash: c307172d7bf8b258cbd56b4ef4abfe6704750358
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92192364"
---
# <a name="getting-started-with-clr-integration"></a>Приступая к работе с интеграцией со средой CLR

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

В этом разделе приводятся общие сведения о пространствах имен и библиотеках, необходимых для компиляции объектов базы данных с помощью [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] интеграции с .NET Framework среды CLR. В этом разделе также показано, как написать, скомпилировать и выполнить простую хранимую процедуру CLR на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.  
  
## <a name="required-namespaces"></a>Необходимые пространства имен  

Компоненты, необходимые для разработки базовых объектов базы данных среды CLR, устанавливаются вместе с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Функции интеграции со средой CLR доступны через сборку под названием system.data.dll, которая является частью платформы .NET Framework. Эту сборку можно найти в глобальном кэше сборок (GAC), а также в каталоге .NET Framework. Ссылка на эту сборку обычно добавляется автоматически и при использовании инструментов с интерфейсом командной строки, и при работе в среде [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio, поэтому нет необходимости добавлять ее вручную.  
  
Сборка system.data.dll содержит следующие пространства имен, необходимые для компиляции объектов базы данных среды CLR:  
  
- `System.Data`  
- `System.Data.Sql`  
- `Microsoft.SqlServer.Server`  
- `System.Data.SqlTypes`  

> [!TIP]
> Загрузка объектов базы данных CLR в Linux поддерживается, но они должны быть построены с помощью .NET Framework (SQL Server интеграция со средой CLR не поддерживает .NET Core). Кроме того, в Linux не поддерживаются сборки CLR с EXTERNAL_ACCESS или ненадежным набором разрешений.

## <a name="writing-a-simple-hello-world-stored-procedure"></a>Создание простой хранимой процедуры «Hello World»  

Скопируйте и вставьте следующий код Visual C# или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic в текстовом редакторе и сохраните его в файле с именем «helloworld.cs» или «helloworld.vb».  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlTypes;  
  
public class HelloWorldProc  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld(out string text)  
    {  
        SqlContext.Pipe.Send("Hello world!" + Environment.NewLine);  
        text = "Hello world!";  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlTypes  
Imports System.Runtime.InteropServices  
  
Public Class HelloWorldProc  
    \<Microsoft.SqlServer.Server.SqlProcedure> _   
    Public Shared  Sub HelloWorld(\<Out()> ByRef text as String)  
        SqlContext.Pipe.Send("Hello world!" & Environment.NewLine)  
        text = "Hello world!"  
    End Sub  
End Class  
  
```  
  
Эта простая программа содержит единственный статический метод общего класса. Этот метод использует два новых класса, **[SqlContext](/dotnet/api/microsoft.sqlserver.server.sqlcontext)** и **[SqlPipe](/dotnet/api/microsoft.sqlserver.server.sqlpipe)**, для создания управляемых объектов базы данных для вывода простого текстового сообщения. Метод также назначает строку "Hello World!" в качестве значения параметра out. Этот метод можно объявить как хранимую процедуру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а затем выполнить так же, как и любую хранимую процедуру [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
Скомпилируйте эту программу как библиотеку, загрузите ее в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и запустите ее как хранимую процедуру.  
  
## <a name="compile-the-hello-world-stored-procedure"></a>Компиляция хранимой процедуры "Hello World"  

В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] распространяемые файлы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework устанавливаются по умолчанию. Эти файлы включают csc.exe и vbc.exe, компиляторы командной строки для программ Visual C# и Visual Basic. Чтобы скомпилировать приведенный образец, измените используемую системную переменную пути и укажите в ней путь к каталогу, содержащему файл csc.exe или vbc.exe. Ниже приведен используемый по умолчанию путь установки .NET Framework.  
  
`C:\Windows\Microsoft.NET\Framework\(version)`  
  
Версия содержит номер версии установленной платформы .NET Framework. Пример:  
  
`C:\Windows\Microsoft.NET\Framework\v4.6.1`

После добавления каталога .NET Framework к пути можно скомпилировать образец хранимой процедуры с созданием сборки с помощью следующей команды. Параметр **/Target** позволяет компилировать его в сборку.  
  
Для файлов с исходным кодом Visual C#:  
  
`csc /target:library helloworld.cs`  
  
 Для файлов с исходным кодом Visual Basic:  
  
`vbc /target:library helloworld.vb`  
  
Эти команды запускают компилятор Visual C# или Visual Basic с использованием параметра /target, задающего построение библиотеки DLL.  
  
## <a name="loading-and-running-the-hello-world-stored-procedure-in-sql-server"></a>Загрузка и выполнение хранимой процедуры «Hello World» в SQL Server  

После успешной компиляции образца процедуры можно провести ее проверку в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Для этого откройте среду [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] и создайте новый запрос, соединившись с подходящей тестовой базой данных (например, к образцу базы данных AdventureWorks).  
  
По умолчанию возможность выполнять код среды CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] отключена. Код CLR можно включить с помощью системной хранимой процедуры **sp_configure** . Дополнительные сведения см. в статье [Enabling CLR Integration](../../../relational-databases/clr-integration/clr-integration-enabling.md).  
  
Создание сборки требуется для того, чтобы можно было получить доступ к хранимой процедуре. В этом примере предполагается, что была создана сборка helloworld.dll в каталоге C:\. Добавьте к запросу следующую инструкцию [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
`CREATE ASSEMBLY helloworld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE`  
  
После создания сборки появляется возможность получить доступ к методу HelloWorld с помощью инструкции создания процедуры. Назовем создаваемую хранимую процедуру «hello»:  
  
```sql
CREATE PROCEDURE hello  
@i nchar(25) OUTPUT  
AS  
EXTERNAL NAME helloworld.HelloWorldProc.HelloWorld  
-- if the HelloWorldProc class is inside a namespace (called MyNS),  
-- the last line in the create procedure statement would be  
-- EXTERNAL NAME helloworld.[MyNS.HelloWorldProc].HelloWorld  
```  
  
После создания процедуры ее можно выполнить как обычную хранимую процедуру на языке [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Выполните следующую команду:  
  
```sql
DECLARE @J nchar(25)  
EXEC hello @J out  
PRINT @J  
```  
  
Это должно привести к появлению следующего вывода в окне сообщений среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
```
Hello world!  
Hello world!  
```  
  
## <a name="removing-the-hello-world-stored-procedure-sample"></a>Удаление образца хранимой процедуры «Hello World»  

После завершения выполнения образца хранимой процедуры эту процедуру и сборку можно удалить из тестовой базы данных.  
  
Вначале удалите процедуру с помощью команды drop procedure.  
  
```sql
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'hello')  
   drop procedure hello  
```  
  
После удаления процедуры можно удалить сборку, содержащую образец кода.  
  
```sql
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'helloworld')  
   drop assembly helloworld  
```  
  
## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения об интеграции со средой CLR в SQL Server см. в следующих статьях:

- [Хранимые процедуры CLR](/dotnet/framework/data/adonet/sql/clr-stored-procedures)
- [Внутрипроцессные расширения SQL Server для ADO.NET](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)
- [Отладка объектов базы данных среды CLR](../../../relational-databases/clr-integration/debugging-clr-database-objects.md)
- [Безопасность интеграции со средой CLR](../../../relational-databases/clr-integration/security/clr-integration-security.md)