---
title: Отладка объектов базы данных CLR | Документация Майкрософт
description: SQL Server обеспечивает поддержку отладки объектов Transact-SQL и CLR в базе данных интеграция SQL Server отладчик с Microsoft Visual Studio отладчиком.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- database objects [CLR integration], debugging
- permissions [CLR integration]
- debugging [CLR integration]
- building database objects [CLR integration], debugging
- common language runtime [SQL Server], debugging
ms.assetid: 1332035c-d6ed-424d-8234-46ad21168319
author: rothja
ms.author: jroth
ms.openlocfilehash: 7af58a109a658a4af60ca49ad6eea401284782ac
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85756312"
---
# <a name="debugging-clr-database-objects"></a>Отладка объектов базы данных среды CLR
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляется поддержка отладки объектов [!INCLUDE[tsql](../../includes/tsql-md.md)] и среды CLR в базе данных. Ключевыми особенностями отладки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] стали простота установки и использования, а также интеграция отладчика SQL Server с отладчиком Microsoft Visual Studio. Более того, процесс отладки охватывает код на всех применяемых языках: пользователи могут беспрепятственно переходить к коду объектов среды CLR из кода [!INCLUDE[tsql](../../includes/tsql-md.md)] и наоборот. Отладчик Transact-SQL в среде SQL Server Management Studio нельзя использовать для отладки управляемых объектов базы данных, но эти объекты можно отлаживать с помощью отладчиков, входящих в состав среды Visual Studio. Отладка управляемого объекта базы данных в Visual Studio поддерживает все обычные средства отладки, такие как шаг с входом и шаг с выходом в процедурах, выполняющихся на сервере. Отладчики могут задавать точки останова, просматривать стек вызова, проверять значения переменных и изменять значения переменных во время отладки. Обратите внимание, что среду Visual Studio .NET 2003 нельзя использовать для программирования или отладки в интеграции со средой CLR. В состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входит предварительно установленная платформа .NET Framework, а Visual Studio .NET 2003 не может использовать сборки .NET Framework версии 2.0.  
  
 Дополнительные сведения об отладке управляемого кода с помощью Visual Studio см. в разделе "[Отладка управляемого кода](https://go.microsoft.com/fwlink/?LinkId=120377)" в документации по Visual Studio.  
  
## <a name="debugging-permissions-and-restrictions"></a>Разрешения и ограничения отладки  
 Отладка — это операция с высокой степенью привилегий, и поэтому в могут быть разрешены только члены предопределенной роли сервера **sysadmin** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 При отладке применяются следующие ограничения.  
  
-   При отладке процедур CLR можно использовать одновременно только один экземпляр отладчика. Это ограничение налагается в связи с тем, что при достижении точки останова выполнение всего кода CLR приостанавливается и возобновляется лишь после прохождения отладчиком этой точки останова. Однако отладку кода [!INCLUDE[tsql](../../includes/tsql-md.md)] можно продолжать в других соединениях. Хотя отладка кода [!INCLUDE[tsql](../../includes/tsql-md.md)] не приводит к приостановке выполнения другого кода на сервере, она может вызывать переход других соединений в состояние ожидания в результате блокировки.  
  
-   Отладка может быть выполнена только для новых соединений, так как перед выполнением соединения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуются сведения о среде клиента и отладчика.  
  
 С учетом указанных ограничений рекомендуется отлаживать код [!INCLUDE[tsql](../../includes/tsql-md.md)] и CLR на тестовом, а не на рабочем сервере.  
  
## <a name="overview-of-debugging-managed-database-objects"></a>Общие сведения об отладке управляемых объектов базы данных  
 Отладка в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] организована на основе модели с учетом соединений. Отладчик может обнаруживать и отлаживать действия только в том клиентском соединении, к которому он присоединен. Функциональные возможности отладчика не ограничиваются типом соединения, поэтому возможна отладка как соединений с потоком табличных данных (TDS), так и HTTP-соединений. Однако [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не позволяет выполнять отладку существующих соединений. Процесс отладки поддерживает общие функции отладки внутри процедур, выполняемых на сервере. Взаимодействие между отладчиком и сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] происходит через модель DCOM.  
  
 Дополнительные сведения и сценарии отладки управляемых хранимых процедур, функций, триггеров, определяемых пользователем типов и статистических выражений см. в разделе "[SQL Server отладка базы данных интеграции со средой CLR](https://go.microsoft.com/fwlink/?LinkId=120378)" документации по Visual Studio.  
  
 Чтобы использовать Visual Studio для удаленной разработки, отладки и разработки, в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть включен протокол TCP/IP. Дополнительные сведения о включении протокола TCP/IP на сервере см. в разделе [Настройка клиентских протоколов](../../database-engine/configure-windows/configure-client-protocols.md).  
  
#### <a name="to-debug-a-managed-database-object"></a>Отладка управляемого объекта базы данных  
  
1.  Откройте среду Microsoft Visual Studio, создайте новый проект [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и установите соединение с базой данных экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Создайте новый тип. В **Обозреватель решений**щелкните правой кнопкой мыши проект, выберите **Добавить** и **новый элемент...** В окне **Добавление нового элемента** выберите **хранимая процедура**, **определяемая пользователем функция**, **определяемый пользователем тип**, **триггер**, **агрегат**или **класс**. Укажите имя исходного файла нового типа и нажмите кнопку **Добавить**.  
  
3.  Добавьте в текстовый редактор код для нового типа. Образец кода для примера хранимой процедуры см. далее в этом разделе.  
  
4.  Добавьте скрипт, который будет тестировать этот тип. В **Обозреватель решений**разверните каталог **TestScripts** , дважды щелкните **Test. SQL** , чтобы открыть исходный файл скрипта теста по умолчанию. Добавьте в текстовый редактор тестовый скрипт, вызывающий отладку кода. Образец скрипта см. ниже.  
  
5.  Поместите одну или несколько точек останова в исходный код. Щелкните правой кнопкой мыши строку кода в текстовом редакторе внутри функции или подпрограммы, которую необходимо отладить, и выберите **точка останова** и **Вставить точку останова**. Точка останова добавится, а строка кода будет выделена красным цветом.  
  
6.  В меню **Отладка** выберите команду **начать отладку** , чтобы скомпилировать, развернуть и протестировать проект. В Test.sql запустится тестовый скрипт и будет вызван управляемый объект базы данных.  
  
7.  Когда на точке останова появится желтая стрелка, обозначающая указатель команд, выполнение кода приостановится и можно будет начать отладку управляемого объекта базы данных. Вы можете **Перейти** в меню **Отладка** , чтобы переместить указатель инструкции на следующую строку кода. Окно **локальные** используется для отслеживания состояния объектов, выделенных указателем инструкций. Переменные можно добавить в окно **Контрольные значения** . Состояние контролируемых переменных можно просмотреть по всему сеансу отладки, а не только в строке кода, выделенной указателем команд. В меню «Отладка» нажмите кнопку «Продолжить», чтобы переместить указатель команд на следующую точку останова или завершить выполнение процедуры, если точек останова больше нет.  
  
### <a name="example"></a>Пример  
 Следующий пример возвращает версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] участнику.  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void GetVersion()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version",  
                                           connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Partial Public Class StoredProcedures   
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub GetVersion()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 Ниже представлен тестовый скрипт, вызывающий хранимую процедуру GetVersion, заданную выше.  
  
```  
EXEC GetVersion  
```  
  
## <a name="see-also"></a>См. также  
 [Основные понятия о программировании интеграции со средой (CLR)](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
