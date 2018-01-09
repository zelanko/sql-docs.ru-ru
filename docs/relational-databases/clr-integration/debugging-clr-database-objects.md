---
title: "Отладка объектов базы данных CLR | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- database objects [CLR integration], debugging
- permissions [CLR integration]
- debugging [CLR integration]
- building database objects [CLR integration], debugging
- common language runtime [SQL Server], debugging
ms.assetid: 1332035c-d6ed-424d-8234-46ad21168319
caps.latest.revision: "46"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 055023bf4c41bad380e1306a2facd7dc884b75ba
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="debugging-clr-database-objects"></a>Отладка объектов базы данных среды CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает поддержку отладки [!INCLUDE[tsql](../../includes/tsql-md.md)] и общеязыковая среда выполнения (CLR) объектов в базе данных. Ключевыми особенностями отладки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] стали простота установки и использования, а также интеграция отладчика SQL Server с отладчиком Microsoft Visual Studio. Более того, процесс отладки охватывает код на всех применяемых языках: пользователи могут беспрепятственно переходить к коду объектов среды CLR из кода [!INCLUDE[tsql](../../includes/tsql-md.md)] и наоборот. Отладчик Transact-SQL в среде SQL Server Management Studio нельзя использовать для отладки управляемых объектов базы данных, но эти объекты можно отлаживать с помощью отладчиков, входящих в состав среды Visual Studio. Отладка управляемого объекта базы данных в Visual Studio поддерживает все обычные средства отладки, такие как шаг с входом и шаг с выходом в процедурах, выполняющихся на сервере. Отладчики могут задавать точки останова, просматривать стек вызова, проверять значения переменных и изменять значения переменных во время отладки. Обратите внимание, что среду Visual Studio .NET 2003 нельзя использовать для программирования или отладки в интеграции со средой CLR. В состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входит предварительно установленная платформа .NET Framework, а Visual Studio .NET 2003 не может использовать сборки .NET Framework версии 2.0.  
  
 Дополнительные сведения об отладке управляемого кода с помощью Visual Studio см. в разделе «[отладки управляемого кода](http://go.microsoft.com/fwlink/?LinkId=120377)» в документации Visual Studio.  
  
## <a name="debugging-permissions-and-restrictions"></a>Разрешения и ограничения отладки  
 Отладка — это операция с высокими привилегиями и поэтому только члены **sysadmin** предопределенной роли сервера могут осуществлять в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 При отладке применяются следующие ограничения.  
  
-   При отладке процедур CLR можно использовать одновременно только один экземпляр отладчика. Это ограничение налагается в связи с тем, что при достижении точки останова выполнение всего кода CLR приостанавливается и возобновляется лишь после прохождения отладчиком этой точки останова. Однако отладку кода [!INCLUDE[tsql](../../includes/tsql-md.md)] можно продолжать в других соединениях. Хотя отладка кода [!INCLUDE[tsql](../../includes/tsql-md.md)] не приводит к приостановке выполнения другого кода на сервере, она может вызывать переход других соединений в состояние ожидания в результате блокировки.  
  
-   Отладка может быть выполнена только для новых соединений, так как перед выполнением соединения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуются сведения о среде клиента и отладчика.  
  
 С учетом указанных ограничений рекомендуется отлаживать код [!INCLUDE[tsql](../../includes/tsql-md.md)] и CLR на тестовом, а не на рабочем сервере.  
  
## <a name="overview-of-debugging-managed-database-objects"></a>Общие сведения об отладке управляемых объектов базы данных  
 Отладка в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] организована на основе модели с учетом соединений. Отладчик может обнаруживать и отлаживать действия только в том клиентском соединении, к которому он присоединен. Функциональные возможности отладчика не ограничиваются типом соединения, поэтому возможна отладка как соединений с потоком табличных данных (TDS), так и HTTP-соединений. Однако [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не позволяет выполнять отладку существующих соединений. Процесс отладки поддерживает общие функции отладки внутри процедур, выполняемых на сервере. Взаимодействие между отладчиком и сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] происходит через модель DCOM.  
  
 Дополнительные сведения об отладке и сценарии управляемые хранимые процедуры, функции, триггеры, определяемые пользователем типы и статистические выражения, в разделе «[отладку по базы данных интеграции SQL Server со средой CLR](http://go.microsoft.com/fwlink/?LinkId=120378)» раздела в Visual Studio документация.  
  
 Чтобы использовать Visual Studio для удаленной разработки, отладки и разработки, в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть включен протокол TCP/IP. Дополнительные сведения о включении протокола TCP/IP на сервере см. в разделе [Настройка клиентских протоколов](../../database-engine/configure-windows/configure-client-protocols.md).  
  
#### <a name="to-debug-a-managed-database-object"></a>Отладка управляемого объекта базы данных  
  
1.  Откройте среду Microsoft Visual Studio, создайте новый проект [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и установите соединение с базой данных экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Создайте новый тип. В **обозревателе решений**, щелкните правой кнопкой мыши проект, выберите **добавить** и **новый элемент...** Из **Добавление нового элемента** выберите **хранимой процедуры**, **пользовательская функция**, **определяемого пользователем типа**,  **Триггер**, **статистические**, или **класса**. Укажите имя для нового типа исходного файла и нажмите кнопку **добавить**.  
  
3.  Добавьте в текстовый редактор код для нового типа. Образец кода для примера хранимой процедуры см. далее в этом разделе.  
  
4.  Добавьте скрипт, который будет тестировать этот тип. В **обозревателе решений**, разверните **TestScripts** дважды щелкните каталог **Test.sql** открыть исходный файл тестового скрипта по умолчанию. Добавьте в текстовый редактор тестовый скрипт, вызывающий отладку кода. Образец скрипта см. ниже.  
  
5.  Поместите одну или несколько точек останова в исходный код. Щелкните правой кнопкой мыши строку кода в редакторе текста внутри функции или подпрограммы, который нужно отладить, и выберите **останова** и **вставить точку останова**. Точка останова добавится, а строка кода будет выделена красным цветом.  
  
6.  В **отладки** последовательно выберите пункты **начать отладку** для компиляции, развертывания и тестирования проекта. В Test.sql запустится тестовый скрипт и будет вызван управляемый объект базы данных.  
  
7.  Когда на точке останова появится желтая стрелка, обозначающая указатель команд, выполнение кода приостановится и можно будет начать отладку управляемого объекта базы данных. Вы можете **шаг с обходом** из **отладки** меню, чтобы переместить указатель команд на следующую строку кода. **Локальные** окно используется для наблюдения за состоянием объектов, выделенных указателем команд. Можно добавить переменные **Контрольные значения** окна. Состояние контролируемых переменных можно просмотреть по всему сеансу отладки, а не только в строке кода, выделенной указателем команд. В меню «Отладка» нажмите кнопку «Продолжить», чтобы переместить указатель команд на следующую точку останова или завершить выполнение процедуры, если точек останова больше нет.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Основные понятия о программировании интеграции со средой (CLR)](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
