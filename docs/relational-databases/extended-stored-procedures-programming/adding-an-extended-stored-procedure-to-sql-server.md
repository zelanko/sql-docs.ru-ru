---
title: Добавление расширенной хранимой процедуры SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], adding
- adding extended stored procedures
- collations [SQL Server], extended stored procedures
ms.assetid: 10f1bb74-3b43-4efd-b7ab-7a85a8600a50
caps.latest.revision: 39
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 44d3315e58a0aecd77219952a45bf77385350626
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="adding-an-extended-stored-procedure-to-sql-server"></a>Добавление на SQL Server расширенной хранимой процедуры
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 DLL-библиотека, которая содержит функции расширенных хранимых процедур, используется как расширение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы установить DLL-Библиотеку, скопируйте файл в каталог, например тот, который содержит стандартные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL-файлы (C:\Program Files\Microsoft SQL Server\MSSQL12.0. *x*\MSSQL\Binn по умолчанию).  
  
 После копирования DLL-библиотеки расширенной хранимой процедуры на сервер, системному администратору [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следует зарегистрировать в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] каждую из функций расширенной хранимой процедуры в DLL-библиотеке. Это выполняется с помощью системной хранимой процедуры sp_addextendedproc.  
  
> [!IMPORTANT]  
>  Перед добавлением расширенной процедуры на сервер и предоставлением разрешения на ее выполнение другим пользователям системному администратору следует тщательно проверить расширенную хранимую процедуру, чтобы убедиться, что она не содержит вредоносного или злонамеренного кода.  Проверяйте все данные, вводимые пользователем. Не осуществляйте объединение пользовательских входных данных до их проверки. Никогда не выполняйте команду, построенную на основании непроверенных пользовательских входных данных.  
  
 Первый параметр sp_addextendedproc указывает имя функции, а второй параметр указывает имя DLL-библиотеки, в которой размещается функция. Рекомендуется указывать полный путь DLL.  
  
> [!IMPORTANT]  
>  Существующие библиотеки DLL, которые не зарегистрированы с полным путем, перестанут работать после обновления до SQL Server 2005 или более поздней версии. Для решения этой проблемы воспользуйтесь хранимой процедурой sp_dropextendedproc для отмены регистрации DLL-библиотеки, а затем выполните их повторную регистрацию процедурой sp_addextendedproc, указывая полный путь доступа.  
  
 Имя функции, передаваемое хранимой процедуре `sp_addextendedproc`, должно полностью совпадать с именем функции в DLL-библиотеке, включая регистр символов. Например, следующая команда регистрирует функцию `xp_hello,`, расположенную в DLL-библиотеке с именем `xp_hello.dll`, в качестве расширенной хранимой процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
sp_addextendedproc 'xp_hello', 'c:\Program Files\Microsoft SQL Server\MSSQL13.0.MSSQLSERVER\MSSQL\Binn\xp_hello.dll';  
```  
  
 Если имя функции, указанное в процедуре `sp_addextendedproc`, не соответствует в точности имени функции в DLL-библиотеке, новое имя будет зарегистрировано в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но это имя будет непригодно для использования. Например несмотря на то что `xp_Hello` регистрируется как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] расширенная хранимая процедура, расположенная в `xp_hello.dll`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не смогут найти такую функцию в DLL-Библиотеке при использовании `xp_Hello` для вызова функции в будущем.  
  
```  
--Register the function (xp_hello) with an initial upper case  
sp_addextendedproc 'xp_Hello', 'c:\xp_hello.dll';  
  
--Use the newly registered name to call the function  
DECLARE @txt varchar(33);  
EXEC xp_Hello @txt OUTPUT;  
  
--This is the error message  
Server: Msg 17750, Level 16, State 1, Procedure xp_Hello, Line 1  
Could not load the DLL xp_hello.dll, or one of the DLLs it references. Reason: 127(The specified procedure could not be found.).  
```  
  
 Если имя функции, указанное в `sp_addextendedproc`, точно соответствует имени функции в DLL-библиотеке, а в параметрах сортировки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не учитывается регистр, пользователь может вызвать расширенную хранимую процедуру с использованием любого сочетания символов нижнего и верхнего регистров в ее имени.  
  
```  
--Register the function (xp_hello)  
sp_addextendedproc 'xp_hello', 'c:\xp_hello.dll';  
  
--The following will succeed in calling xp_hello  
DECLARE @txt varchar(33);  
EXEC xp_Hello @txt OUTPUT;  
  
DECLARE @txt varchar(33);  
EXEC xp_HelLO @txt OUTPUT;  
  
DECLARE @txt varchar(33);  
EXEC xp_HELLO @txt OUTPUT;  
```  
  
 Если в параметрах сортировки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учитывается регистр, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не сможет вызвать расширенную хранимую процедуру, даже если она была зарегистрирована точно с тем же именем и параметрами сортировки, как функция в DLL-библиотеке, если при вызове процедуры ее имя указано в другом регистре символов.  
  
```  
--Register the function (xp_hello)  
sp_addextendedproc 'xp_hello', 'c:\xp_hello.dll';  
  
--The following will result in an error  
DECLARE @txt varchar(33);  
EXEC xp_HELLO @txt OUTPUT;  
  
--This is the error  
Server: Msg 2812, Level 16, State 62, Line 1  
```  
  
 Останавливать и перезапускать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не обязательно.  
  
## <a name="see-also"></a>См. также  
 [sp_addextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
