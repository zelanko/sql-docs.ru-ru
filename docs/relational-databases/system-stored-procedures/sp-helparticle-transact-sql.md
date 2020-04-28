---
title: sp_helparticle (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helparticle_TSQL
- sp_helparticle
helpviewer_keywords:
- sp_helparticle
ms.assetid: 9c4a1a88-56f1-45a0-890c-941b8e0f0799
author: stevestein
ms.author: sstein
ms.openlocfilehash: e1e71d3795b233ec335cf01848fa3b226a6ebde0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68771099"
---
# <a name="sp_helparticle-transact-sql"></a>sp_helparticle (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Отображает сведения о статье. Эта хранимая процедура выполняется на издателе в базе данных публикации. Для издателей Oracle данная хранимая процедура выполняется распространителем для любой базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helparticle [ @publication = ] 'publication'   
    [ , [ @article = ] 'article' ]  
    [ , [ @returnfilter = ] returnfilter ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @found = ] found OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @article = ] 'article'`Имя статьи в публикации. Аргумент *article* имеет тип **sysname**и значение по **%** умолчанию. Если *статья* не указана, возвращаются сведения обо всех статьях для указанной публикации.  
  
`[ @returnfilter = ] returnfilter`Указывает, должно ли возвращаться предложение фильтра. *ретурнфилтер* имеет **бит**и значение по умолчанию **1**, которое возвращает предложение фильтра.  
  
`[ @publisher = ] 'publisher'`Указывает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, отличного от. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  не следует указывать *Издатель* при запросе сведений о статье, опубликованной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателем.  
  
`[ @found = ] found OUTPUT`Только для внутреннего использования.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Идентификатор статьи**|**int**|Идентификатор статьи.|  
|**article name**|**sysname**|Имя статьи.|  
|**base object**|**nvarchar (257)**|Имя базовой таблицы, заданной в статье или в хранимой процедуре.|  
|**Объект destination**|**sysname**|Имя целевой таблицы (таблицы подписки).|  
|**synchronization object**|**nvarchar (257)**|Имя представления, определяющего опубликованную статью.|  
|**type**|**smallint**|Тип статьи:<br /><br /> **1** = на основе журнала.<br /><br /> **3** = журнал на основе журнала с ручным фильтром.<br /><br /> **5** = Журнал основан на представлении, выполняемом вручную.<br /><br /> **7** = на основе журнала с ручным фильтром и с ручным просмотром.<br /><br /> **8** = выполнение хранимой процедуры.<br /><br /> **24** = выполнение сериализуемых хранимых процедур.<br /><br /> **32** = хранимая процедура (только схема).<br /><br /> **64** = представление (только схема).<br /><br /> **96** = агрегатная функция (только схема).<br /><br /> **128** = функция (только схема).<br /><br /> **257** = индексированное представление на основе журнала.<br /><br /> **259** = индексированное представление на основе журнала с ручным фильтром.<br /><br /> **261** = индексированное представление на основе журнала с ручным представлением.<br /><br /> **263** = индексированное представление на основе журнала с ручным фильтром и ручным представлением.<br /><br /> **320** = индексированное представление (только схема).<br /><br />|  
|**status**|**tinyint**|Может быть результатом [& (побитовое и)](../../t-sql/language-elements/bitwise-and-transact-sql.md) для одного или нескольких или следующих свойств статьи:<br /><br /> **0x00** = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> **0x01** = статья активна.<br /><br /> **0x08** = включить имя столбца в инструкции INSERT.<br /><br /> **0x16** = использовать параметризованные инструкции.<br /><br /> **0x32** = использовать параметризованные инструкции и включать имя столбца в инструкции INSERT.|  
|**Фильтрация**|**nvarchar (257)**|Хранимая процедура, используемая для горизонтальной фильтрации таблиц. Данная хранимая процедура должна быть создана с помощью предложения FOR REPLICATION.|  
|**nописание**|**nvarchar(255)**|Описание статьи.|  
|**insert_command**|**nvarchar(255)**|Тип команды репликации, используемый при репликационной вставке в статьи таблицы. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**update_command**|**nvarchar(255)**|Тип команды репликации, используемый при репликационном обновлении статей таблицы. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**delete_command**|**nvarchar(255)**|Тип команды репликации, используемый при репликационном удалении в статьях таблицы. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**creation script path**|**nvarchar(255)**|Путь и имя скрипта схемы статьи, используемого для создания целевых таблиц.|  
|**vertical partition**|**bit**|Указывает, включено ли вертикальное секционирование для статьи; значение **1** означает, что вертикальное секционирование включено.|  
|**pre_creation_cmd**|**tinyint**|Команда, выполняемая перед инструкциями DROP TABLE, DELETE TABLE и TRUNCATE.|  
|**filter_clause**|**ntext**|Предложение WHERE задает горизонтальную фильтрацию.|  
|**schema_option**|**Binary (8)**|Битовая карта параметра создания схемы для заданной статьи. Полный список значений **schema_option** см. в разделе [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).|  
|**dest_owner**|**sysname**|Имя владельца целевого объекта.|  
|**source_owner**|**sysname**|Владелец исходного объекта.|  
|**unqua_source_object**|**sysname**|Имя исходного объекта без учета имени его владельца.|  
|**sync_object_owner**|**sysname**|Владелец представления, определяющего опубликованную статью. .|  
|**unqualified_sync_object**|**sysname**|Имя представления, определяющего опубликованную статью, без учета имени владельца.|  
|**filter_owner**|**sysname**|Владелец фильтра.|  
|**unqua_filter**|**sysname**|Имя фильтра без учета имени его владельца.|  
|**auto_identity_range**|**int**|Флаг, показывающий включение автоматической обработки диапазонов идентификаторов для публикации при ее создании. **1** означает, что автоматический диапазон идентификаторов включен; **0** означает, что она отключена.|  
|**publisher_identity_range**|**int**|Размер диапазона для диапазона идентификаторов на издателе, если в статье *identityrangemanagementoption* задано значение **Auto** или **auto_identity_range** задано значение **true**.|  
|**identity_range**|**bigint**|Размер диапазона для диапазона идентификаторов на подписчике, если в статье *identityrangemanagementoption* задано значение **Auto** или **auto_identity_range** установлен в **значение true**.|  
|**значениями**|**bigint**|Процентное значение, показывающее момент, когда агент распространителя выделяет новый диапазон идентификаторов.|  
|**identityrangemanagementoption**|**int**|Указывает способ управления диапазоном идентификаторов для статьи.|  
|**fire_triggers_on_snapshot**|**bit**|Используется в случае, когда реплицированные пользовательские триггеры срабатывают при применении исходного моментального снимка:<br /><br /> **1** = выполняются пользовательские триггеры.<br /><br /> **0** = пользовательские триггеры не выполняются.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_helparticle** используется в репликации моментальных снимков и репликации транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** , предопределенной роли базы данных **db_owner** или списка доступа к публикации для текущей публикации могут выполнять **sp_helparticle**.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_helptranarticle](../../relational-databases/replication/codesnippet/tsql/sp-helparticle-transact-_1.sql)]  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств статьи](../../relational-databases/replication/publish/view-and-modify-article-properties.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
