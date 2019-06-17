---
title: Характеристики выполнения расширенных хранимых процедур | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], executing
- executing extended stored procedures [SQL Server]
ms.assetid: 6fe1f7e8-cc02-49df-8a2a-d47a96ec3567
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: d21f002ca6b7ea185df2e01f66abf0e1ef5cfd1b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62512226"
---
# <a name="execution-characteristics-of-extended-stored-procedures"></a>Характеристики выполнения расширенных хранимых процедур
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 Выполнение расширенных хранимых процедур имеет следующие характеристики:  
  
-   Расширенная хранимая процедура выполняется в контексте безопасности [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   расширенная хранимая процедура выполняется в пространстве процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];  
  
-   поток, связанный с выполнением расширенной хранимой процедуры, тот же, что используется для клиентского соединения.  
  
    > [!IMPORTANT]  
    >  Прежде чем добавить расширенные хранимые процедуры на сервер и предоставить разрешение на их выполнение другим пользователям, системный администратор должен тщательно проверить каждую хранимую процедуру, чтобы убедиться, что она не содержит вредоносного или злонамеренного кода.  
  
-  
  
 После расширенной хранимой процедуры, при загрузке библиотеки DLL, библиотеки DLL остается загруженной в адресном пространстве сервера, пока [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] остановлена или администратор явно выгружает библиотеку DLL с помощью инструкции DBCC *DLL_name* (FREE).  
  
 Расширенная хранимая процедура может выполняться в [!INCLUDE[tsql](../../includes/tsql-md.md)] как хранимая процедура с помощью инструкции EXECUTE:  
  
```  
EXECUTE @retval = xp_extendedProcName @param1, @param2 OUTPUT  
```  
  
## <a name="parameters"></a>Параметры  
 \@ *retval*  
 Возвращаемое значение.  
  
 \@ *содержит param1*  
 Входной параметр.  
  
 \@ *Param2*  
 Входной и (или) выходной параметр.  
  
> [!CAUTION]  
>  Расширенные хранимые процедуры увеличивают производительность и расширяют возможности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако из-за того, что DLL-библиотека расширенной хранимой процедуры и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] совместно используют одно и то же адресное пространство, проблемная процедура может отрицательно повлиять на работу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Хотя исключения, вызываемые DLL-библиотеками расширенных хранимых процедур, обрабатываются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], тем не менее можно повредить области данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В целях безопасности добавлять расширенные хранимые процедуры к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут только системные администраторы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перед установкой эти процедуры следует тщательно протестировать.  
  
## <a name="see-also"></a>См. также  
 [Программирование расширенных хранимых процедур](database-engine-extended-stored-procedures-programming.md)   
 [Запрос расширенных хранимых процедур, установленных в SQL Server](querying-extended-stored-procedures-installed-in-sql-server.md)  
  
  
