---
description: xp_sqlmaint (Transact-SQL)
title: xp_sqlmaint (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_sqlmaint
- xp_sqlmaint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_sqlmaint
ms.assetid: bda66e1b-6bbd-49be-b86e-37efc920e912
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cfe66be84a9f631422c624eaf65152569d0405bd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419188"
---
# <a name="xp_sqlmaint-transact-sql"></a>xp_sqlmaint (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Вызывает служебную программу **sqlmaint** со строкой, содержащей параметры **sqlmaint**. Программа **sqlmaint** выполняет набор операций обслуживания для одной или нескольких баз данных.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_sqlmaint 'switch_string'     
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *switch_string* **"**  
 — Это строка, содержащая переключатели программы **sqlmaint** . Ключи и их значения должны разделяться пробелами.  
  
 **-?** Недопустимый параметр для **xp_sqlmaint**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Отсутствует. Возвращает ошибку, если программа **sqlmaint** завершается сбоем.  
  
## <a name="remarks"></a>Remarks  
 Если эта процедура вызывается пользователем, вошедшим в систему с проверкой подлинности SQL Server, то перед выполнением параметры **-U "***login_ID***"** и **-P "***password***** " добавляются в начало *switch_string* . Если пользователь вошел в систему с проверкой подлинности Windows, *switch_string* передается без изменений в **sqlmaint**.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере процедура `xp_sqlmaint` вызывает программу `sqlmaint` для выполнения проверки целостности, создания файла отчета и обновления данных `msdb.dbo.sysdbmaintplan_history`.  
  
```  
EXEC xp_sqlmaint '-D AdventureWorks2012 -PlanID 02A52657-D546-11D1-9D8A-00A0C9054212   
   -Rpt "C:\Program Files\Microsoft SQL Server\MSSQL\LOG\DBMaintPlan2.txt" -WriteHistory  -CkDB -CkAl';   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The command(s) executed successfully.  
```  
  
## <a name="see-also"></a>См. также:  
 [sqlmaint, программа](../../tools/sqlmaint-utility.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
