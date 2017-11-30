---
title: "xp_sqlmaint (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xp_sqlmaint
- xp_sqlmaint_TSQL
dev_langs: TSQL
helpviewer_keywords: xp_sqlmaint
ms.assetid: bda66e1b-6bbd-49be-b86e-37efc920e912
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b32c6c32d3af26713713d513fa3c8255cfd3ef9d
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="xpsqlmaint-transact-sql"></a>xp_sqlmaint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вызовы **sqlmaint** строку, содержащую программу **sqlmaint**коммутаторов. **Sqlmaint** выполняет набор операций обслуживания с одной или нескольких баз данных.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_sqlmaint 'switch_string'     
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *switch_string* **"**  
 Строка, содержащая **sqlmaint** ключи программы. Ключи и их значения должны разделяться пробелами.  
  
 **-?** параметр не действует для **xp_sqlmaint**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет. Возвращает сообщение об ошибке, если **sqlmaint** программа завершается с ошибкой.  
  
## <a name="remarks"></a>Замечания  
 Если эта процедура вызывается пользователем, в систему с использованием проверки подлинности SQL Server, **- U "***login_id***»** и **-P"**  *пароль***»** добавляются к *switch_string* перед выполнением. Если пользователь вошел в систему с проверкой подлинности Windows, *switch_string* передаются без изменения **sqlmaint**.  
  
## <a name="permissions"></a>Permissions  
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
 [Программа sqlmaint](../../tools/sqlmaint-utility.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
