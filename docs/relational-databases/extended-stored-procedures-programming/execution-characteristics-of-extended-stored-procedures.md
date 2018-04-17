---
title: Характеристики выполнения расширенных хранимых процедур | Документы Microsoft
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
- extended stored procedures [SQL Server], executing
- executing extended stored procedures [SQL Server]
ms.assetid: 6fe1f7e8-cc02-49df-8a2a-d47a96ec3567
caps.latest.revision: 33
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c95aaba427984447539f6c8213e7f69eb3b10b3a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="execution-characteristics-of-extended-stored-procedures"></a>Характеристики выполнения расширенных хранимых процедур
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 Выполнение расширенных хранимых процедур имеет следующие характеристики:  
  
-   Функция расширенная хранимая процедура выполняется в контексте безопасности [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   расширенная хранимая процедура выполняется в пространстве процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];  
  
-   поток, связанный с выполнением расширенной хранимой процедуры, тот же, что используется для клиентского соединения.  
  
    > [!IMPORTANT]  
    >  Прежде чем добавить расширенные хранимые процедуры на сервер и предоставить разрешение на их выполнение другим пользователям, системный администратор должен тщательно проверить каждую хранимую процедуру, чтобы убедиться, что она не содержит вредоносного или злонамеренного кода.  
  
-  
  
 После расширенной хранимой процедуры загрузки библиотеки DLL, библиотеки DLL остается загруженной в адресном пространстве сервера до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] остановлена или администратор явно не выгрузит библиотеки DLL с помощью инструкции DBCC *DLL_name* (FREE).  
  
 Расширенная хранимая процедура может выполняться в [!INCLUDE[tsql](../../includes/tsql-md.md)] как хранимая процедура с помощью инструкции EXECUTE:  
  
```  
EXECUTE @retval = xp_extendedProcName @param1, @param2 OUTPUT  
```  
  
## <a name="parameters"></a>Параметры  
 @ *retval*  
 Возвращаемое значение.  
  
 @ *содержит param1*  
 Входной параметр.  
  
 @ *Param2*  
 Входной и (или) выходной параметр.  
  
> [!CAUTION]  
>  Расширенные хранимые процедуры увеличивают производительность и расширяют возможности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако из-за того, что DLL-библиотека расширенной хранимой процедуры и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] совместно используют одно и то же адресное пространство, проблемная процедура может отрицательно повлиять на работу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Хотя исключения, вызываемые DLL-библиотеками расширенных хранимых процедур, обрабатываются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], тем не менее можно повредить области данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В целях безопасности добавлять расширенные хранимые процедуры к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут только системные администраторы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перед установкой эти процедуры следует тщательно протестировать.  
  
## <a name="see-also"></a>См. также  
 [Программирование расширенных хранимых процедур](../../relational-databases/extended-stored-procedures-programming/database-engine-extended-stored-procedures-programming.md)   
 [Запрос расширенных хранимых процедур, установленных в SQL Server](../../relational-databases/extended-stored-procedures-programming/querying-extended-stored-procedures-installed-in-sql-server.md)  
  
  
