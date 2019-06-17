---
title: Изменение свойств публикации и статьи | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- modifying article properties
- modifying publication properties
- administering replication, properties
- publications [SQL Server replication], changing properties
- articles [SQL Server replication], properties
ms.assetid: f7df51ef-c088-4efc-b247-f91fb2c6ff32
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d0e5b67288e9cc9d0491f30dc98b3edf9c01c0f1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62662808"
---
# <a name="change-publication-and-article-properties"></a>Изменение свойств публикации и статьи
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  После того как публикация создана, большинство свойств публикаций и статей можно изменить, но для некоторых изменений требуется, повторное создание моментального снимка и/или повторная инициализация подписок. В этом разделе содержатся сведения обо всех свойствах, требуемых для одного или обоих этих действий (если они изменяются).  
  
## <a name="publication-properties-for-snapshot-and-transactional-replication"></a>Свойства публикации для репликации моментальных снимков и репликации транзакций.  
  
|Описание|Хранимая процедура|Свойства|Требования|  
|-----------------|----------------------|----------------|------------------|  
|Изменение формата моментального снимка.|**sp_changepublication**|**sync_method**|Создание моментального снимка.|  
|Изменение расположения моментального снимка.|**sp_changepublication**|**alt_snapshot_folder**<br /><br /> **snapshot_in_defaultfolder**|Создание моментального снимка.|  
|Изменение расположения моментального снимка.|**sp_changedistpublisher, хранимая процедура**|**working_directory**|Создание моментального снимка.|  
|Изменение сжатия моментального снимка.|**sp_changepublication**|**compress_snapshot**|Создание моментального снимка.|  
|Изменение параметров FTP-протокола для моментального снимка.|**sp_changepublication**|**enabled_for_internet**<br /><br /> **ftp_address**<br /><br /> **ftp_login**<br /><br /> **ftp_password**<br /><br /> **ftp_port**<br /><br /> **ftp_subdirectory**|Создание моментального снимка.|  
|Изменение расположения скрипта, запускаемого перед моментальным снимком или после него.|**sp_changepublication**|**pre_snapshot_script**<br /><br /> **post_snapshot_script**|Создание моментального снимка (требуется также при изменении содержимого скрипта).<br /><br /> Для применения нового скрипта к подписчику требуется повторная инициализация.|  
|Включение или выключение поддержки для подписчиков, отличных от подписчиков [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|**sp_changepublication**|**is_enabled_for_het_sub**|Создание моментального снимка.|  
|Изменение отчета о конфликтах подписок, обновляемых посредством очередей|**sp_changepublication**|**centralized_conflicts**|Может быть изменена только при отсутствии активных подписок.|  
|Изменение политики разрешения конфликтов для подписок, обновляемых посредством очередей|**sp_changepublication**|**conflict_policy**|Может быть изменена только при отсутствии активных подписок.|  
  
## <a name="article-properties-for-snapshot-and-transactional-replication"></a>Свойства статьи для репликации моментальных снимков и репликации транзакций.  
  
|Описание|Хранимая процедура|Свойства|Требования|  
|-----------------|----------------------|----------------|------------------|  
|Удаление статьи|**sp_droparticle**|Все параметры.|Статьи могут быть удалены до создания подписок. С помощью хранимых процедур можно удалить подписку на статью. При использовании [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]вся подписка должна быть удалена, создана повторно и синхронизирована. Дополнительные сведения см. в статье [Добавление и удаление статей в существующих публикациях](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).|  
|Изменение фильтра столбцов.|**sp_articlecolumn**|**@column**<br /><br /> **@operation**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Добавление фильтра строк.|**sp_articlefilter**|Все параметры.|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Удаление фильтра строк.|**sp_articlefilter**|**@article**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение фильтра строк.|**sp_articlefilter**|**@filter_clause**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение фильтра строк.|**sp_changearticle**|**фильтр**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение параметров схемы.|**sp_changearticle**|**schema_option**|Создание моментального снимка.|  
|Изменение порядка обработки таблиц на подписчике до применения моментального снимка.|**sp_changearticle**|**pre_creation_cmd**|Создание моментального снимка.|  
|Изменение состояния статьи|**sp_changearticle**|**status**|Создание моментального снимка.|  
|Изменение команды INSERT, UPDATE или DELETE.|**sp_changearticle**|**ins_cmd**<br /><br /> **upd_cmd**<br /><br /> **del_cmd**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение имени целевой таблицы|**sp_changearticle**|**dest_table**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение владельца (схемы) целевой таблицы.|**sp_changearticle**|**destination_owner**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение сопоставление типов данных (применимо только к публикации Oracle).|**sp_changearticlecolumndatatype**|**@type**<br /><br /> **@length**<br /><br /> **@precision**<br /><br /> **@scale**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
  
## <a name="publication-properties-for-merge-replication"></a>Свойства публикации для репликации слиянием  
  
|Описание|Хранимая процедура|Свойства|Требования|  
|-----------------|----------------------|----------------|------------------|  
|Изменение формата моментального снимка|**sp_changemergepublication**|**sync_mode**|Создание моментального снимка.|  
|Изменение расположения моментального снимка.|**sp_changemergepublication**|**alt_snapshot_folder**<br /><br /> **snapshot_in_defaultfolder**|Создание моментального снимка.|  
|Изменение расположения моментального снимка.|**sp_changedistpublisher, хранимая процедура**|**working_directory**|Создание моментального снимка.|  
|Изменение сжатия моментального снимка|**sp_changemergepublication**|**compress_snapshot**|Создание моментального снимка.|  
|Изменение любых параметров протокола FTP для моментального снимка|**sp_changemergepublication**|**enabled_for_internet**<br /><br /> **ftp_address**<br /><br /> **ftp_login**<br /><br /> **ftp_password**<br /><br /> **ftp_port**<br /><br /> **ftp_subdirectory**|Создание моментального снимка.|  
|Изменение скриптов, запускаемых перед моментальным снимком или после него.|**sp_changemergepublication**|**pre_snapshot_script**<br /><br /> **post_snapshot_script**|Создание моментального снимка (требуется также при изменении содержимого скрипта).<br /><br /> Для применения нового скрипта к подписчику требуется повторная инициализация.|  
|Добавление фильтра соединения или логической записи.|**sp_addmergefilter**|Все параметры.|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Удаление фильтра соединения или логической записи.|**sp_dropmergefilter**|Все параметры.|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение фильтра соединения или логической записи.|**sp_changemergefilter**|**@property**<br /><br /> **@value**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Отключение использования параметризованных фильтров (включение параметризованных фильтров не требует никаких специальных действий).|**sp_changemergepublication**|Значение **false** для **dynamic_filters**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Включение или выключение использования предварительно вычисляемых секций.|**sp_changemergepublication**|**use_partition_groups**|Создание моментального снимка.|  
|Включение или выключение оптимизации секций [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)].|**sp_changemergepublication**|**keep_partition_changes**|Повторная инициализация подписок.|  
|Включение или выключение проверки секций подписчика.|**sp_changemergepublication**|**validate_subscriber_info**|Повторная инициализация подписок.|  
|Изменение уровня совместимости публикации до 80sp3 или ниже.|**sp_changemergepublication**|**publication_compatibility_level**|Создание моментального снимка.|  
  
## <a name="article-properties-for-merge-replication"></a>Свойства статьи для репликации слиянием  
  
|Описание|Хранимая процедура|Свойства|Требования|  
|-----------------|----------------------|----------------|------------------|  
|Удаление статьи с последним параметризованным фильтром в публикации.|**sp_dropmergearticle**|Все параметры|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Удаление статьи, являющейся родителем в фильтре соединения или в логической записи (это побочный эффект удаления соединения).|**sp_dropmergearticle**|Все параметры|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Удаление статьи при прочих обстоятельствах.|**sp_dropmergearticle**|Все параметры|Создание моментального снимка.|  
|Включение в состав ранее не опубликованного фильтра столбцов.|**sp_mergearticlecolumn**|**@column**<br /><br /> **@operation**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Добавление, удаление или изменение фильтра строк.|**sp_changemergearticle**|**subset_filterclause**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.<br /><br /> Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.<br /><br /> Если статья не используется ни в каких фильтрах соединения, статью можно удалить и создать ее заново с другим фильтром строк, который не требует повторной инициализации всей подписки. Дополнительные сведения о добавлении и удалении статей см. в статье [Добавление и удаление статей в существующих публикациях](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).|  
|Изменение параметров схемы.|**sp_changemergearticle**|**schema_option**|Создание моментального снимка.|  
|Изменение детализации отслеживания изменений от уровня столбцов до уровня строк (обратное изменение не требует дополнительных действий).|**sp_changemergearticle**|Значение **false** для **column_tracking**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение режима, определяющего, будут ли проверяться разрешения до применения на издателе инструкций, созданных на подписчике.|**sp_changemergearticle**|**check_permissions**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Включение или выключение подписок, доступных только для загрузки (изменение других параметров отгрузки не требует каких-либо особых действий).|**sp_changemergearticle**|Изменение значения **subscriber_upload_options** на или с **2**|Повторная инициализация подписок.|  
|Изменение владельца целевой таблицы.|**sp_changemergearticle**|**destination_owner**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
  
## <a name="see-also"></a>См. также:  
 [Вопросы и ответы об администрировании репликации](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)   
 [Создание и применение моментального снимка](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Повторная инициализация подписок](../../../relational-databases/replication/reinitialize-subscriptions.md)   
 [sp_addmergefilter (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_articlecolumn (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_articlefilter (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_changearticlecolumndatatype (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql.md)   
 [sp_changedistpublisher (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_changemergearticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_changemergefilter (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_changemergepublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_changepublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_droparticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_dropmergearticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md)   
 [sp_dropmergefilter (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_mergearticlecolumn (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md)  
  
  
