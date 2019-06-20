---
title: sp_helpxactsetjob (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpxactsetjob
- sp_helpxactsetjob_TSQL
helpviewer_keywords:
- sp_helpxactsetjob
ms.assetid: 242cea3e-e6ac-4f84-a072-b003b920eb33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7402fcc825e6f537703268c1fd3fead9c88b1f5e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62959614"
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
 [ **@publisher** =] **"***издателя***"**  
 Имя отличного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, к которой принадлежит задание. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**jobnumber**|**int**|Номер задания Oracle.|  
|**lastdate**|**varchar(22)**|Последняя дата выполнения задания.|  
|**thisdate**|**varchar(22)**|Время изменения.|  
|**nextdate**|**varchar(22)**|Следующая дата, когда задание будет запущено.|  
|**разбить**|**varchar(1)**|Флаг, означающий неудачное выполнение задания.|  
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
  
## <a name="remarks"></a>Примечания  
 **sp_helpxactsetjob** используется в репликации моментальных снимков и репликации транзакций для издателей Oracle.  
  
 **sp_helpxactsetjob** всегда возвращает текущие параметры для задания Xactset (HREPL_XactSetJob) на издателе. Если задание Xactset в данные момент находится в очереди заданий, то оно дополнительно возвращает атрибуты задания из представления словаря данных USER_JOB, созданного под учетной записью администратора на издателе Oracle.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_helpxactsetjob**.  
  
## <a name="see-also"></a>См. также  
 [Configure the Transaction Set Job for an Oracle Publisher](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)  (Настройка задания для набора транзакции в издателе Oracle)  
 [sp_publisherproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)  
  
  
