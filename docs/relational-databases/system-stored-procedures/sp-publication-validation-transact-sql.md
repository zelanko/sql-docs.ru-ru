---
title: sp_publication_validation (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_publication_validation
- sp_publication_validation_TSQL
helpviewer_keywords:
- sp_publication_validation
ms.assetid: 06be2363-00c0-4936-97c1-7347f294a936
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 124d5d14f810a32e32ce92cbb96afe4569804c67
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537176"
---
# <a name="sppublicationvalidation-transact-sql"></a>sp_publication_validation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Запускает запрос на проверку правильности всех статей в указанной публикации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_publication_validation [ @publication = ] 'publication'  
    [ , [ @rowcount_only = ] type_of_check_requested ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [**@publication=**] **"**_публикации"_  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [**@rowcount_only=**] *rowcount_only*  
 Указывает, возвращать ли только количество строк таблицы. *rowcount_only* — **smallint** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Рассчитать контрольную сумму в формате [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0.<br /><br /> Примечание. Если статья отфильтрована горизонтально, вместо операции расчета контрольной суммы выполняется операция подсчета строк.|  
|**1** (по умолчанию)|Выполнить проверку только количества строк.|  
|**2**|Выполнить проверку количества строк и двоичной контрольной суммы.<br /><br /> Примечание. Для подписчиков версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 выполняется только проверка количества строк.|  
  
 [**@full_or_fast=**] *full_or_fast*  
 Метод, применяемый для подсчета числа строк. *full_or_fast* — **tinyint** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Выполняет полный подсчет с помощью функции COUNT(*).|  
|**1**|Выполняет быстрый подсчет из **sysindexes.rows**. Подсчет строк в [sys.sysindexes](../../relational-databases/system-compatibility-views/sys-sysindexes-transact-sql.md) выполняется гораздо быстрее, чем подсчет строк в фактической таблице. Тем не менее так как [sys.sysindexes](../../relational-databases/system-compatibility-views/sys-sysindexes-transact-sql.md) задержкой обновлены, количество строк может оказаться неточным.|  
|**2** (по умолчанию)|Выполняет быстрый подсчет по условию, при котором сначала используется быстрый метод. Если быстрый метод дает неточные результаты, переключается на полный подсчет. Если *expected_rowcount* имеет значение NULL и хранимая процедура используется для получения значения, полная функция COUNT(*) всегда используется.|  
  
`[ @shutdown_agent = ] shutdown_agent` Является ли агент распространителя завершен немедленно после завершения проверки. *shutdown_agent* — **бит**, значение по умолчанию **0**. Если **0**, агент репликации не завершает работу. Если **1**, агент репликации завершает работу после проверки последней статье.  
  
`[ @publisher = ] 'publisher'` Указывает, отличный от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует использовать при запросе проверки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_publication_validation** используется в репликации транзакций.  
  
 **sp_publication_validation** можно вызвать в любое время после активации статей, связанных с публикацией. Данная процедура может запускаться вручную (единовременно) либо в составе регулярных планируемых заданий по проверке данных.  
  
 Если приложения с немедленно обновляемыми, **sp_publication_validation** могут быть обнаружены случайные ошибки. **sp_publication_validation** сначала вычисляет количество строк или контрольной суммы на издателе, а затем на подписчике. Значения контрольных сумм и количества строк для издателя и подписчика могут различаться, так как после подсчета на издателе, но до подсчета на подписчике может сработать триггер немедленного обновления. Чтобы исключить возможность изменения значений для подписчика и издателя во время проверки публикации, остановите службу координатора распределенных транзакций Microsoft (MS DTC) на издателе во время проверки.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_publication_validation**.  
  
## <a name="see-also"></a>См. также  
 [Проверка данных на подписчике](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)   
 [sp_table_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
