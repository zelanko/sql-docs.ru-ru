---
title: sp_article_validation (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_article_validation_TSQL
- sp_article_validation
helpviewer_keywords:
- sp_article_validation
ms.assetid: 44e7abcd-778c-4728-a03e-7e7e78d3ce22
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6f5ee076163ff3cf0f69daab7ceff115bf5876a6
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769024"
---
# <a name="sparticlevalidation-transact-sql"></a>sp_article_validation (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Инициирует запрос проверки данных для указанной статьи. Эта хранимая процедура выполняется на издателе в базе данных публикации и на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_article_validation [ @publication = ] 'publication'  
    [ , [ @article = ] 'article' ]  
    [ , [ @rowcount_only = ] type_of_check_requested ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @subscription_level = ] subscription_level ]  
    [ , [ @reserved = ] reserved ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации, в которой находится статья. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @article = ] 'article'`Имя статьи для проверки. Аргумент *article* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @rowcount_only = ] type_of_check_requested`Указывает, возвращается ли только количество строк для таблицы. *type_of_check_requested* имеет значение **smallint**и значение по умолчанию **1**.  
  
 Если значение **равно 0**, то необходимо выполнить [!INCLUDE[msCoName](../../includes/msconame-md.md)] контрольную сумму количества строк и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7,0.  
  
 Если значение равно **1**, выполняется только проверка количества строк.  
  
 Если значение равно **2**, то выполняется проверка количества строк и двоичной контрольной суммы.  
  
`[ @full_or_fast = ] full_or_fast`Метод, используемый для вычисления количества строк. *full_or_fast* имеет тип **tinyint**и может принимать одно из следующих значений.  
  
|**Значение**|**Описание**|  
|---------------|---------------------|  
|**0**|Выполняет полный подсчет при помощи функции COUNT(*).|  
|**1**|Выполняет быстрое подсчет из **sysindexes. Rows**. Подсчет строк в **sysindexes** выполняется быстрее, чем подсчет строк в реальной таблице. Однако **sysindexes** обновляется с отложенным обновлением, и количество строк может быть неточным.|  
|**2** (по умолчанию)|Выполняет условный быстрый подсчет, при котором сначала применяется быстрый метод, Если быстрый метод дает неточные результаты, переключается на полный подсчет. Если *expected_rowcount* имеет значение NULL и хранимая процедура используется для получения значения, всегда используется полный счетчик (*).|  
  
`[ @shutdown_agent = ] shutdown_agent`Указывает, должен ли агент распространителя немедленно завершить работу после завершения проверки. *shutdown_agent* имеет **бит**и значение по умолчанию **0**. Если значение **равно 0**, агент распространения не завершает работу. Если значение равно **1**, агент распространения завершает работу после проверки статьи.  
  
`[ @subscription_level = ] subscription_level`Указывает, выбрана ли проверка набором подписчиков. *subscription_level* имеет **бит**и значение по умолчанию **0**. Если значение **равно 0**, то проверка применяется ко всем подписчикам. Если значение равно **1**, проверка применяется только к подмножеству подписчиков, указанных в вызовах **sp_marksubscriptionvalidation** в текущей открытой транзакции.  
  
`[ @reserved = ] reserved` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @publisher = ] 'publisher'`Указывает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, отличного от. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  *Издатель* не должен использоваться при запросе проверки на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_article_validation** используется в репликации транзакций.  
  
 **sp_article_validation** вызывает сбор сведений о проверке в указанной статье и отправляет запрос проверки в журнал транзакций. Когда агент распространителя получает этот запрос, он сравнивает сведения для проверки, указанные в запросе, с таблицей подписчика. Результаты проверки отображаются в мониторе репликации и в виде предупреждений агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 Только пользователи с разрешением SELECT все разрешения на исходную таблицу для проверяемой статьи могут выполнять **sp_article_validation**.  
  
## <a name="see-also"></a>См. также  
 [Проверка реплицированных данных](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_marksubscriptionvalidation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-marksubscriptionvalidation-transact-sql.md)   
 [sp_publication_validation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md)   
 [sp_table_validation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
