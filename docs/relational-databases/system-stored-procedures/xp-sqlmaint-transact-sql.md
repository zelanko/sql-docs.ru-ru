---
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
manager: craigg
ms.openlocfilehash: 2157462ca1f9509034f33208cce7aed2983ae4f2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47746522"
---
# <a name="xpsqlmaint-transact-sql"></a>xp_sqlmaint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вызовы **sqlmaint** утилиту строка, содержащая **sqlmaint**коммутаторов. **Sqlmaint** выполняет набор операций обслуживания с одной или нескольких баз данных.  
  
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
 Нет. Возвращает сообщение об ошибке, если **sqlmaint** программа завершается ошибкой.  
  
## <a name="remarks"></a>Примечания  
 Если эта процедура вызывается пользователем, в систему с использованием проверки подлинности SQL Server, **- U "***login_id***"** и **-P "***пароль***"** коммутаторов добавляются к *switch_string* перед выполнением. Если пользователь вошел в систему с проверкой подлинности Windows, *switch_string* передаются без изменения **sqlmaint**.  
  
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
  
## <a name="see-also"></a>См. также  
 [Программа sqlmaint](../../tools/sqlmaint-utility.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
