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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9f5a32c9706947471908966be59378a0d34147e1
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85899437"
---
# <a name="sp_helpxactsetjob-transact-sql"></a>sp_helpxactsetjob (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отображает сведения о задании набора транзакций для издателя Oracle. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpxactsetjob [ @publisher = ] 'publisher'   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'`Имя издателя, не являющегося [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателем, которому принадлежит задание. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**jobnumber**|**int**|Номер задания Oracle.|  
|**LASTDATE**|**varchar (22)**|Последняя дата выполнения задания.|  
|**thisdate**|**varchar (22)**|Время изменения.|  
|**nextdate**|**varchar (22)**|Следующая дата, когда задание будет запущено.|  
|**broken**|**varchar(1)**|Флаг, означающий неудачное выполнение задания.|  
|**пределах**|**varchar (200)**|Интервал для задания.|  
|**сбоев**|**int**|Количество неудачных выполнений для задания.|  
|**xactsetjobwhat**|**varchar (200)**|Имя процедуры, выполняемой заданием.|  
|**xactsetjob**|**varchar(1)**|Показывает состояние задания, может быть одним из следующих:<br /><br /> **1** — задание включено.<br /><br /> **0** — задание отключено.|  
|**xactsetlonginterval**|**int**|Длительный интервал для задания.|  
|**xactsetlongthreshold**|**int**|Высокий порог для задания.|  
|**xactsetshortinterval**|**int**|Короткий интервал для задания.|  
|**xactsetshortthreshold**|**int**|Низкий порог для задания.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_helpxactsetjob** используется в репликации моментальных снимков и репликации транзакций для издателей Oracle.  
  
 **sp_helpxactsetjob** всегда возвращает текущие параметры для задания набора транзакций (HREPL_XactSetJob) на издателе. Если задание Xactset в данные момент находится в очереди заданий, то оно дополнительно возвращает атрибуты задания из представления словаря данных USER_JOB, созданного под учетной записью администратора на издателе Oracle.  
  
## <a name="permissions"></a>Разрешения  
 Только член предопределенной роли сервера **sysadmin** может выполнять **sp_helpxactsetjob**.  
  
## <a name="see-also"></a>См. также  
 [Настройка задания набора транзакций для издателя Oracle &#40;программирование репликации на языке Transact-SQL&#41;](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
 [sp_publisherproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)  
  
  
