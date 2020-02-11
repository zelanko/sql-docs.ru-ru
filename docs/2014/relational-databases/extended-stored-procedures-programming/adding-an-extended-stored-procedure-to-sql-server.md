---
title: Добавление расширенной хранимой процедуры в SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], adding
- adding extended stored procedures
- collations [SQL Server], extended stored procedures
ms.assetid: 10f1bb74-3b43-4efd-b7ab-7a85a8600a50
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3a5e5ab2d0dba0d7d39fcf3223f0aeec5ab6a058
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62512352"
---
# <a name="adding-an-extended-stored-procedure-to-sql-server"></a>Добавление на SQL Server расширенной хранимой процедуры
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Вместо этого используйте интеграцию со средой CLR.  
  
 DLL-библиотека, которая содержит функции расширенных хранимых процедур, используется как расширение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы установить библиотеку DLL, скопируйте файл в каталог, например в тот, который содержит стандартные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файлы DLL (C:\PROGRAM Files\Microsoft SQL Server\MSSQL12.0.* x*\MSSQL\Binn по умолчанию).  
  
 После копирования DLL-библиотеки расширенной хранимой процедуры на сервер, системному администратору [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следует зарегистрировать в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] каждую из функций расширенной хранимой процедуры в DLL-библиотеке. Это выполняется с помощью системной хранимой процедуры sp_addextendedproc.  
  
> [!IMPORTANT]  
>  Перед добавлением расширенной процедуры на сервер и предоставлением разрешения на ее выполнение другим пользователям системному администратору следует тщательно проверить расширенную хранимую процедуру, чтобы убедиться, что она не содержит вредоносного или злонамеренного кода.  Проверяйте все данные, вводимые пользователем. Не осуществляйте объединение пользовательских входных данных до их проверки. Никогда не выполняйте команду, построенную на основании непроверенных пользовательских входных данных.  
  
 Первый параметр sp_addextendedproc указывает имя функции, а второй параметр указывает имя DLL-библиотеки, в которой размещается функция. Рекомендуется указывать полный путь DLL.  
  
> [!IMPORTANT]  
>  Существующие библиотеки DLL, которые не зарегистрированы с полным путем, перестанут работать после обновления до SQL Server 2005 или более поздней версии. Для решения этой проблемы воспользуйтесь хранимой процедурой sp_dropextendedproc для отмены регистрации DLL-библиотеки, а затем выполните их повторную регистрацию процедурой sp_addextendedproc, указывая полный путь доступа.  
  
 Имя функции, передаваемое хранимой процедуре `sp_addextendedproc`, должно полностью совпадать с именем функции в DLL-библиотеке, включая регистр символов. Например, следующая команда регистрирует функцию `xp_hello,`, расположенную в DLL-библиотеке с именем `xp_hello.dll`, в качестве расширенной хранимой процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
sp_addextendedproc 'xp_hello', 'c:\Program Files\Microsoft SQL Server\MSSQL12.0.MSSQLSERVER\MSSQL\Binn\xp_hello.dll';  
```  
  
 Если имя функции, указанное в процедуре `sp_addextendedproc`, не соответствует в точности имени функции в DLL-библиотеке, новое имя будет зарегистрировано в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но это имя будет непригодно для использования. Например, `xp_Hello` хотя регистрируется как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] расширенная хранимая процедура, расположенная в `xp_hello.dll`, не сможет найти функцию в библиотеке DLL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] если вы используете `xp_Hello` для вызова функции позже.  
  
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
  
## <a name="see-also"></a>См. также:  
 [sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
