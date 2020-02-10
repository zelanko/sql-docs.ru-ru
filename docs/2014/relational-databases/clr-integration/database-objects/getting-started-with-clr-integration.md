---
title: начало работы с интеграцией со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
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
manager: craigg
ms.openlocfilehash: db3a72facf1676360e7c338663facac66840a113
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62874119"
---
# <a name="getting-started-with-clr-integration"></a>Приступая к работе с интеграцией со средой CLR
  В этом разделе приводятся общие сведения о пространствах имен и библиотеках, необходимых для [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] компиляции объектов базы данных с помощью интеграции с .NET Framework среды CLR. В этом разделе также показано, как написать, скомпилировать и выполнить простую хранимую процедуру CLR на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.  
  
## <a name="required-namespaces"></a>Необходимые пространства имен  
 Начиная с [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)]. Функции интеграции со средой CLR доступны через сборку под названием system.data.dll, которая является частью платформы .NET Framework. Эту сборку можно найти в глобальном кэше сборок (GAC), а также в каталоге .NET Framework. Ссылка на эту сборку обычно добавляется автоматически и при использовании инструментов с интерфейсом командной строки, и при работе в среде [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio, поэтому нет необходимости добавлять ее вручную.  
  
 Сборка system.data.dll содержит следующие пространства имен, необходимые для компиляции объектов базы данных среды CLR:  
  
 `System.Data`  
  
 `System.Data.Sql`  
  
 `Microsoft.SqlServer.Server`  
  
 `System.Data.SqlTypes`  
  
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
    <Microsoft.SqlServer.Server.SqlProcedure> _   
    Public Shared  Sub HelloWorld(<Out()> ByRef text as String)  
        SqlContext.Pipe.Send("Hello world!" & Environment.NewLine)  
        text = "Hello world!"  
    End Sub  
End Class  
  
```  
  
 Эта простая программа содержит единственный статический метод общего класса. В методе используются два новых класса, `SqlContext` и `SqlPipe`, позволяющие создать управляемые объекты базы данных для вывода простого текстового сообщения. Метод также назначает строку "Hello World!" в качестве значения параметра out. Этот метод может быть объявлен как хранимая процедура в [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] хранимой процедуре.  
  
 После этого достаточно скомпилировать эту программу как библиотеку, загрузить ее в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и выполнить как хранимую процедуру.  
  
## <a name="compiling-the-hello-world-stored-procedure"></a>Компилирование хранимой процедуры «Hello World»  
 [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)].NET Framework файлы распространения по умолчанию. Эти файлы включают csc.exe и vbc.exe, компиляторы командной строки для программ Visual C# и Visual Basic. Чтобы скомпилировать приведенный образец, измените используемую системную переменную пути и укажите в ней путь к каталогу, содержащему файл csc.exe или vbc.exe. Ниже приведен используемый по умолчанию путь установки .NET Framework.  
  
```  
C:\Windows\Microsoft.NET\Framework\(version)  
```  
  
 Версия содержит номер версии установленной платформы .NET Framework. Пример:  
  
```  
C:\Windows\Microsoft.NET\Framework\v2.0.31113  
```  
  
 После добавления каталога .NET Framework к пути можно скомпилировать образец хранимой процедуры с созданием сборки с помощью следующей команды. Параметр `/target` позволяет скомпилировать код в виде сборки.  
  
 Для файлов с исходным кодом Visual C#:  
  
```  
csc /target:library helloworld.cs   
```  
  
 Для файлов с исходным кодом Visual Basic:  
  
```  
vbc /target:library helloworld.vb  
```  
  
 Эти команды запускают компилятор Visual C# или Visual Basic с использованием параметра /target, задающего построение библиотеки DLL.  
  
## <a name="loading-and-running-the-hello-world-stored-procedure-in-sql-server"></a>Загрузка и выполнение хранимой процедуры «Hello World» в SQL Server  
 После успешной компиляции образца процедуры можно протестировать ее в [!INCLUDE[ssNoVersion](../../../includes/ssmanstudiofull-md.md)] и создать новый запрос, подключившись к подходящей тестовой базе данных (например, образцу базы данных AdventureWorks).  
  
 По умолчанию возможность выполнять код среды CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] отключена. Код CLR можно включить с помощью системной хранимой процедуры **sp_configure** . Дополнительные сведения см. в статье [Enabling CLR Integration](../clr-integration-enabling.md).  
  
 Создание сборки требуется для того, чтобы можно было получить доступ к хранимой процедуре. В этом примере предполагается, что была создана сборка helloworld.dll в каталоге C:\. Добавьте к запросу следующую инструкцию [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
```  
CREATE ASSEMBLY helloworld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE  
```  
  
 После создания сборки появляется возможность получить доступ к методу HelloWorld с помощью инструкции создания процедуры. Назовем создаваемую хранимую процедуру «hello»:  
  
```  
  
CREATE PROCEDURE hello  
@i nchar(25) OUTPUT  
AS  
EXTERNAL NAME helloworld.HelloWorldProc.HelloWorld  
-- if the HelloWorldProc class is inside a namespace (called MyNS),  
-- the last line in the create procedure statement would be  
-- EXTERNAL NAME helloworld.[MyNS.HelloWorldProc].HelloWorld  
```  
  
 После создания процедуры ее можно выполнить как обычную хранимую процедуру на языке [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Выполните следующую команду.  
  
```  
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
  
```  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'hello')  
   drop procedure hello  
```  
  
 После удаления процедуры можно удалить сборку, содержащую образец кода.  
  
```  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'helloworld')  
   drop assembly helloworld  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры CLR](../../../database-engine/dev-guide/clr-stored-procedures.md)   
 [SQL Server встроенных расширений ADO.NET](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)   
 [Отладка объектов базы данных CLR](../debugging-clr-database-objects.md)   
 [Безопасность интеграции со средой CLR](../security/clr-integration-security.md)  
  
  
