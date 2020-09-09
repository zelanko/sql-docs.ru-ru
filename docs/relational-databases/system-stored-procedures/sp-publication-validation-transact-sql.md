---
description: sp_publication_validation (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: dccdb0f168b7b1e113a38c64a111e35e5bf62d77
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89535013"
---
# <a name="sp_publication_validation-transact-sql"></a>sp_publication_validation (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

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
`[ @publication = ] 'publication'` Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @rowcount_only = ] 'rowcount_only'` Указывает, следует ли возвращать только ROWCOUNT для таблицы. *rowcount_only* имеет значение **smallint** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Рассчитать контрольную сумму в формате [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0.<br /><br /> Примечание. Если статья отфильтрована горизонтально, то вместо операции контрольной суммы выполняется операция ROWCOUNT.|  
|**1** (по умолчанию)|Выполнить проверку только количества строк.|  
|**2**|Выполнить проверку количества строк и двоичной контрольной суммы.<br /><br /> Примечание. для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков версии 7,0 выполняется только проверка количества строк.|  
  
`[ @full_or_fast = ] 'full_or_fast'` Метод, используемый для вычисления количества строк. *full_or_fast* имеет тип **tinyint** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Выполняет полный подсчет с помощью функции COUNT(*).|  
|**1**|Выполняет быстрое подсчет из **sysindexes. Rows**. Подсчет строк в [sys.sysиндексах](../../relational-databases/system-compatibility-views/sys-sysindexes-transact-sql.md) выполняется гораздо быстрее, чем подсчет строк в реальной таблице. Однако, поскольку [sys.sysиндексы](../../relational-databases/system-compatibility-views/sys-sysindexes-transact-sql.md) отложенно обновляются, количество строк может быть неточным.|  
|**2** (по умолчанию)|Выполняет быстрый подсчет по условию, при котором сначала используется быстрый метод. Если быстрый метод дает неточные результаты, переключается на полный подсчет. Если *expected_rowcount* имеет значение NULL и хранимая процедура используется для получения значения, всегда используется полный счетчик (*).|  
  
`[ @shutdown_agent = ] 'shutdown_agent'` Указывает, следует ли завершать работу агент распространения сразу после завершения проверки. *shutdown_agent* имеет **бит**и значение по умолчанию **0**. Если значение **равно 0**, агент репликации не завершает работу. Если значение равно **1**, агент репликации завершает работу после проверки последней статьи.  
  
`[ @publisher = ] 'publisher'` Указывает издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  *Издатель* не должен использоваться при запросе проверки на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_publication_validation** используется в репликации транзакций.  
  
 **sp_publication_validation** можно вызвать в любое время после активации статей, связанных с публикацией. Данная процедура может запускаться вручную (единовременно) либо в составе регулярных планируемых заданий по проверке данных.  
  
 Если у приложения есть немедленно обновляемые подписчики, **sp_publication_validation** может обнаружить ложные ошибки. **sp_publication_validation** сначала вычисляет количество строк или контрольную сумму на издателе, а затем на подписчике. Значения контрольных сумм и количества строк для издателя и подписчика могут различаться, так как после подсчета на издателе, но до подсчета на подписчике может сработать триггер немедленного обновления. Чтобы исключить возможность изменения значений для подписчика и издателя во время проверки публикации, остановите службу координатора распределенных транзакций Microsoft (MS DTC) на издателе во время проверки.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_publication_validation**.  
  
## <a name="see-also"></a>См. также  
 [Проверка данных на подписчике](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)   
 [sp_table_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
