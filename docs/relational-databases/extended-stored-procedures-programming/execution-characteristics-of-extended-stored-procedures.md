---
description: Характеристики выполнения расширенных хранимых процедур
title: Характеристики выполнения расширенных хранимых процедур
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], executing
- executing extended stored procedures [SQL Server]
ms.assetid: 6fe1f7e8-cc02-49df-8a2a-d47a96ec3567
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: 23162895a2e2461fbd6f0f0abbe71341ce2fbf91
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460873"
---
# <a name="execution-characteristics-of-extended-stored-procedures"></a>Характеристики выполнения расширенных хранимых процедур
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 Выполнение расширенных хранимых процедур имеет следующие характеристики:  
  
-   Функция расширенной хранимой процедуры выполняется в контексте безопасности [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   расширенная хранимая процедура выполняется в пространстве процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];  
  
-   поток, связанный с выполнением расширенной хранимой процедуры, тот же, что используется для клиентского соединения.  
  
    > [!IMPORTANT]  
    >  Прежде чем добавить расширенные хранимые процедуры на сервер и предоставить разрешение на их выполнение другим пользователям, системный администратор должен тщательно проверить каждую хранимую процедуру, чтобы убедиться, что она не содержит вредоносного или злонамеренного кода.  
  
-  
  
 После загрузки библиотеки DLL расширенной хранимой процедуры библиотека DLL остается загруженной в адресное пространство сервера до тех пор, пока [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не будет остановлена или администратор явно выгрузит БИБЛИОТЕКУ DLL с помощью команды DBCC *DLL_name* (Free).  
  
 Расширенная хранимая процедура может выполняться в [!INCLUDE[tsql](../../includes/tsql-md.md)] как хранимая процедура с помощью инструкции EXECUTE:  
  
```  
EXECUTE @retval = xp_extendedProcName @param1, @param2 OUTPUT  
```  
  
## <a name="parameters"></a>Параметры  
 \@ *retval*  
 Возвращаемое значение.  
  
 \@*param1*  
 Входной параметр.  
  
 \@*Param2*  
 Входной и (или) выходной параметр.  
  
> [!CAUTION]  
>  Расширенные хранимые процедуры увеличивают производительность и расширяют возможности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако из-за того, что DLL-библиотека расширенной хранимой процедуры и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] совместно используют одно и то же адресное пространство, проблемная процедура может отрицательно повлиять на работу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Хотя исключения, вызываемые DLL-библиотеками расширенных хранимых процедур, обрабатываются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], тем не менее можно повредить области данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В целях безопасности добавлять расширенные хранимые процедуры к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут только системные администраторы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перед установкой эти процедуры следует тщательно протестировать.  
  
## <a name="see-also"></a>См. также:  
 [Программирование расширенных хранимых процедур](../../relational-databases/extended-stored-procedures-programming/database-engine-extended-stored-procedures-programming.md)   
 [Запрос расширенных хранимых процедур, установленных в SQL Server](../../relational-databases/extended-stored-procedures-programming/querying-extended-stored-procedures-installed-in-sql-server.md)  
  
  
