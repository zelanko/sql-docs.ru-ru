---
title: Отладка объектов базы данных CLR (ru) Документы Майкрософт
description: Сервер S'L предоставляет поддержку для отладки объектов Transact-S'L и CLR в базе данных, интегрирующей отладку сервера S'L с отладчиком Microsoft Visual Studio.
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
ms.openlocfilehash: 71a766dc473c1bef47a8104ae76c0e70bd8b31b8
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488401"
---
# <a name="debugging-clr-database-objects"></a>Отладка объектов базы данных среды CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляется поддержка отладки объектов [!INCLUDE[tsql](../../includes/tsql-md.md)] и среды CLR в базе данных. Ключевыми особенностями отладки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] стали простота установки и использования, а также интеграция отладчика SQL Server с отладчиком Microsoft Visual Studio. Более того, процесс отладки охватывает код на всех применяемых языках: пользователи могут беспрепятственно переходить к коду объектов среды CLR из кода [!INCLUDE[tsql](../../includes/tsql-md.md)] и наоборот. Отладчик Transact-SQL в среде SQL Server Management Studio нельзя использовать для отладки управляемых объектов базы данных, но эти объекты можно отлаживать с помощью отладчиков, входящих в состав среды Visual Studio. Отладка управляемого объекта базы данных в Visual Studio поддерживает все обычные средства отладки, такие как шаг с входом и шаг с выходом в процедурах, выполняющихся на сервере. Отладчики могут задавать точки останова, просматривать стек вызова, проверять значения переменных и изменять значения переменных во время отладки. Обратите внимание, что среду Visual Studio .NET 2003 нельзя использовать для программирования или отладки в интеграции со средой CLR. В состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входит предварительно установленная платформа .NET Framework, а Visual Studio .NET 2003 не может использовать сборки .NET Framework версии 2.0.  
  
 Подробнее об отладке управляемого кода с помощью Visual Studio читайте в материале[«Отладка управляемого кода»](https://go.microsoft.com/fwlink/?LinkId=120377)в документации Visual Studio.  
  
## <a name="debugging-permissions-and-restrictions"></a>Разрешения и ограничения отладки  
 Отладка является очень привилегированной операцией, и поэтому только члены **сисадмина** фиксированной роли сервера могут сделать это в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 При отладке применяются следующие ограничения.  
  
-   При отладке процедур CLR можно использовать одновременно только один экземпляр отладчика. Это ограничение налагается в связи с тем, что при достижении точки останова выполнение всего кода CLR приостанавливается и возобновляется лишь после прохождения отладчиком этой точки останова. Однако отладку кода [!INCLUDE[tsql](../../includes/tsql-md.md)] можно продолжать в других соединениях. Хотя отладка кода [!INCLUDE[tsql](../../includes/tsql-md.md)] не приводит к приостановке выполнения другого кода на сервере, она может вызывать переход других соединений в состояние ожидания в результате блокировки.  
  
-   Отладка может быть выполнена только для новых соединений, так как перед выполнением соединения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуются сведения о среде клиента и отладчика.  
  
 С учетом указанных ограничений рекомендуется отлаживать код [!INCLUDE[tsql](../../includes/tsql-md.md)] и CLR на тестовом, а не на рабочем сервере.  
  
## <a name="overview-of-debugging-managed-database-objects"></a>Общие сведения об отладке управляемых объектов базы данных  
 Отладка в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] организована на основе модели с учетом соединений. Отладчик может обнаруживать и отлаживать действия только в том клиентском соединении, к которому он присоединен. Функциональные возможности отладчика не ограничиваются типом соединения, поэтому возможна отладка как соединений с потоком табличных данных (TDS), так и HTTP-соединений. Однако [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не позволяет выполнять отладку существующих соединений. Процесс отладки поддерживает общие функции отладки внутри процедур, выполняемых на сервере. Взаимодействие между отладчиком и сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] происходит через модель DCOM.  
  
 Для получения дополнительной информации и сценариев отладки управляемых сохраненных процедур, функций, триггеров, типов и агрегированных элементов, определяемых пользователями, см. в документации Visual Studio подробнее об этом читайте в материале[«Отладка интеграции СЕРВЕРа CLR».](https://go.microsoft.com/fwlink/?LinkId=120378)  
  
 Чтобы использовать Visual Studio для удаленной разработки, отладки и разработки, в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть включен протокол TCP/IP. Для получения дополнительной информации о включении протокола TCP/IP на [сервере](../../database-engine/configure-windows/configure-client-protocols.md)см.  
  
#### <a name="to-debug-a-managed-database-object"></a>Отладка управляемого объекта базы данных  
  
1.  Откройте среду Microsoft Visual Studio, создайте новый проект [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и установите соединение с базой данных экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Создайте новый тип. В **Solution Explorer**, правой кнопкой мыши проекта, выберите **Добавить** и **новый пункт ...** Из окна **Добавить новый элемент** выберите **Сохраненную процедуру**, **Пользователь-Определенный функции**, **Пользователь-Определенный тип**, **Триггер**, **Агрегат**, или **класс**. Укажите имя исходного файла нового типа и нажмите **Добавить**.  
  
3.  Добавьте в текстовый редактор код для нового типа. Образец кода для примера хранимой процедуры см. далее в этом разделе.  
  
4.  Добавьте скрипт, который будет тестировать этот тип. В **Solution Explorer**расширьте каталог **TestScripts** дважды щелкните **Test.sql,** чтобы открыть исходный файл исходного сценария теста по умолчанию. Добавьте в текстовый редактор тестовый скрипт, вызывающий отладку кода. Образец скрипта см. ниже.  
  
5.  Поместите одну или несколько точек останова в исходный код. Нажмите правой кнопкой мыши на строку кода в текстовом редакторе, в функции или рутины, которые вы хотите отладить, и выберите **Breakpoint** и **Вставить Breakpoint.** Точка останова добавится, а строка кода будет выделена красным цветом.  
  
6.  В меню **Debug** выберите **Start Debugging** для компиляции, развертывания и тестирования проекта. В Test.sql запустится тестовый скрипт и будет вызван управляемый объект базы данных.  
  
7.  Когда на точке останова появится желтая стрелка, обозначающая указатель команд, выполнение кода приостановится и можно будет начать отладку управляемого объекта базы данных. Вы можете **перейти** из меню **Debug,** чтобы продвинуть указатель инструкции к следующей строке кода. Окно **Locals** используется для наблюдения за состоянием объектов, в настоящее время выделенных указателем инструкции. Переменные могут быть добавлены в окно **Watch.** Состояние контролируемых переменных можно просмотреть по всему сеансу отладки, а не только в строке кода, выделенной указателем команд. В меню «Отладка» нажмите кнопку «Продолжить», чтобы переместить указатель команд на следующую точку останова или завершить выполнение процедуры, если точек останова больше нет.  
  
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
  
  
