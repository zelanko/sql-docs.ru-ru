---
title: "sp_helpxactsetjob (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_helpxactsetjob
- sp_helpxactsetjob_TSQL
helpviewer_keywords: sp_helpxactsetjob
ms.assetid: 242cea3e-e6ac-4f84-a072-b003b920eb33
caps.latest.revision: "19"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 52fb4f08d51379368a99647a3e2a1cbe86c8fba5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpxactsetjob-transact-sql"></a>sp_helpxactsetjob (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает сведения о задании набора транзакций для издателя Oracle. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpxactsetjob [ @publisher = ] 'publisher'   
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publisher**  =] **"***издатель***"**  
 Имя издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которому принадлежит задача. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**jobnumber**|**int**|Номер задания Oracle.|  
|**lastdate**|**varchar(22)**|Последняя дата выполнения задания.|  
|**thisdate**|**varchar(22)**|Время изменения.|  
|**nextdate**|**varchar(22)**|Следующая дата, когда задание будет запущено.|  
|**Неработающие**|**varchar(1)**|Флаг, означающий неудачное выполнение задания.|  
|**интервал**|**varchar(200)**|Интервал для задания.|  
|**сбои**|**int**|Количество неудачных выполнений для задания.|  
|**xactsetjobwhat**|**varchar(200)**|Имя процедуры, выполняемой заданием.|  
|**xactsetjob**|**varchar(1)**|Показывает состояние задания, может быть одним из следующих:<br /><br /> **1** -задание включено.<br /><br /> **0** -задание отключено.|  
|**xactsetlonginterval**|**int**|Длительный интервал для задания.|  
|**xactsetlongthreshold**|**int**|Высокий порог для задания.|  
|**xactsetshortinterval**|**int**|Короткий интервал для задания.|  
|**xactsetshortthreshold**|**int**|Низкий порог для задания.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_helpxactsetjob** используется в репликации моментальных снимков и репликации транзакций для издателей Oracle.  
  
 **sp_helpxactsetjob** всегда возвращает текущие параметры для задания Xactset (HREPL_XactSetJob) на издателе. Если задание Xactset в данные момент находится в очереди заданий, то оно дополнительно возвращает атрибуты задания из представления словаря данных USER_JOB, созданного под учетной записью администратора на издателе Oracle.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_helpxactsetjob**.  
  
## <a name="see-also"></a>См. также:  
 [Configure the Transaction Set Job for an Oracle Publisher](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)  (Настройка задания для набора транзакции в издателе Oracle)  
 [sp_publisherproperty &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)  
  
  
