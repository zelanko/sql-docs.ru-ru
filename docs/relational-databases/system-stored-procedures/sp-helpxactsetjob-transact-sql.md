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
ms.openlocfilehash: 0fdd70480a63e334aa3e178d19287b30937e2f53
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056788"
---
# <a name="sp_helpxactsetjob-transact-sql"></a>sp_helpxactsetjob (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает сведения о задании набора транзакций для издателя Oracle. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpxactsetjob [ @publisher = ] 'publisher'   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'` — имя издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которому принадлежит задание. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Data type|Описание|  
|-----------------|---------------|-----------------|  
|**жобнумбер**|**int**|Номер задания Oracle.|  
|**LASTDATE**|**varchar (22)**|Последняя дата выполнения задания.|  
|**сисдате**|**varchar (22)**|Время изменения.|  
|**некстдате**|**varchar (22)**|Следующая дата, когда задание будет запущено.|  
|**рабочие**|**varchar (1)**|Флаг, означающий неудачное выполнение задания.|  
|**пределах**|**varchar (200)**|Интервал для задания.|  
|**сбоев**|**int**|Количество неудачных выполнений для задания.|  
|**ксактсетжобвхат**|**varchar (200)**|Имя процедуры, выполняемой заданием.|  
|**параметре xactsetjob**|**varchar (1)**|Показывает состояние задания, может быть одним из следующих:<br /><br /> **1** — задание включено.<br /><br /> **0** — задание отключено.|  
|**ксактсетлонгинтервал**|**int**|Длительный интервал для задания.|  
|**ксактсетлонгсрешолд**|**int**|Высокий порог для задания.|  
|**ксактсетшортинтервал**|**int**|Короткий интервал для задания.|  
|**ксактсетшортсрешолд**|**int**|Низкий порог для задания.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpxactsetjob** используется в репликации моментальных снимков и репликации транзакций для издателей Oracle.  
  
 **sp_helpxactsetjob** всегда возвращает текущие параметры для задания набора транзакций (HREPL_XactSetJob) на издателе. Если задание Xactset в данные момент находится в очереди заданий, то оно дополнительно возвращает атрибуты задания из представления словаря данных USER_JOB, созданного под учетной записью администратора на издателе Oracle.  
  
## <a name="permissions"></a>Разрешения  
 Только член предопределенной роли сервера **sysadmin** может выполнять **sp_helpxactsetjob**.  
  
## <a name="see-also"></a>См. также статью  
 [Configure the Transaction Set Job for an Oracle Publisher](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)  (Настройка задания для набора транзакции в издателе Oracle)  
 [sp_publisherproperty &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)  
  
  
