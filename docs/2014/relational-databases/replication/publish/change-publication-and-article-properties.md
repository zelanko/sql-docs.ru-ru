---
title: Изменение свойств публикации и статьи | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: c43c81612ffd851d7ea0e0679f79f3c8fec91037
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73882350"
---
# <a name="change-publication-and-article-properties"></a>Изменение свойств публикации и статьи
  После того как публикация создана, большинство свойств публикаций и статей можно изменить, но для некоторых изменений требуется, повторное создание моментального снимка и/или повторная инициализация подписок. В этом разделе содержатся сведения обо всех свойствах, требуемых для одного или обоих этих действий (если они изменяются).  
  
## <a name="publication-properties-for-snapshot-and-transactional-replication"></a>Свойства публикации для репликации моментальных снимков и репликации транзакций.  
  
|Description|Хранимая процедура|Свойства|Требования|  
|-----------------|----------------------|----------------|------------------|  
|Изменение формата моментального снимка.|**sp_changepublication**|**sync_method**|Создание моментального снимка.|  
|Изменение расположения моментального снимка.|**sp_changepublication**|**alt_snapshot_folder**<br /><br /> **snapshot_in_defaultfolder**|Создание моментального снимка.|  
|Изменение расположения моментального снимка.|**sp_changedistpublisher, хранимая процедура**|**working_directory**|Создание моментального снимка.|  
|Изменение сжатия моментального снимка.|**sp_changepublication**|**compress_snapshot**|Создание моментального снимка.|  
|Изменение параметров FTP-протокола для моментального снимка.|**sp_changepublication**|**enabled_for_internet**<br /><br /> **ftp_address**<br /><br /> **ftp_login**<br /><br /> **ftp_password**<br /><br /> **ftp_port**<br /><br /> **ftp_subdirectory**|Создание моментального снимка.|  
|Изменение расположения скрипта, запускаемого перед моментальным снимком или после него.|**sp_changepublication**|**pre_snapshot_script**<br /><br /> **post_snapshot_script**|Создание моментального снимка (требуется также при изменении содержимого скрипта).<br /><br /> Для применения нового скрипта к подписчику требуется повторная инициализация.|  
|Включение или отключение поддержки для[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] подписчиков, отличных от.|**sp_changepublication**|**is_enabled_for_het_sub**|Создание моментального снимка.|  
|Изменение отчета о конфликтах подписок, обновляемых посредством очередей|**sp_changepublication**|**centralized_conflicts**|Может быть изменена только при отсутствии активных подписок.|  
|Изменение политики разрешения конфликтов для подписок, обновляемых посредством очередей|**sp_changepublication**|**conflict_policy**|Может быть изменена только при отсутствии активных подписок.|  
  
## <a name="article-properties-for-snapshot-and-transactional-replication"></a>Свойства статьи для репликации моментальных снимков и репликации транзакций.  
  
|Description|Хранимая процедура|Свойства|Требования|  
|-----------------|----------------------|----------------|------------------|  
|Удаление статьи|**sp_droparticle**|Все параметры.|Статьи могут быть удалены до создания подписок. С помощью хранимых процедур можно удалить подписку на статью. При использовании [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]вся подписка должна быть удалена, создана повторно и синхронизирована. Дополнительные сведения см. в статье [Добавление и удаление статей в существующих публикациях](add-articles-to-and-drop-articles-from-existing-publications.md).|  
|Изменение фильтра столбцов.|**sp_articlecolumn**|**\@рубрик**<br /><br /> **\@операцию**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Добавление фильтра строк.|**sp_articlefilter**|Все параметры.|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Удаление фильтра строк.|**sp_articlefilter**|**\@рассмотрен**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение фильтра строк.|**sp_articlefilter**|**\@filter_clause**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение фильтра строк.|**sp_changearticle**|**Фильтрация**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение параметров схемы.|**sp_changearticle**|**schema_option**|Создание моментального снимка.|  
|Изменение порядка обработки таблиц на подписчике до применения моментального снимка.|**sp_changearticle**|**pre_creation_cmd**|Создание моментального снимка.|  
|Изменение состояния статьи|**sp_changearticle**|**состояние**|Создание моментального снимка.|  
|Изменение команды INSERT, UPDATE или DELETE.|**sp_changearticle**|**ins_cmd**<br /><br /> **upd_cmd**<br /><br /> **del_cmd**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение имени целевой таблицы|**sp_changearticle**|**dest_table**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение владельца (схемы) целевой таблицы.|**sp_changearticle**|**destination_owner**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение сопоставление типов данных (применимо только к публикации Oracle).|**sp_changearticlecolumndatatype**|**\@Тип**<br /><br /> **\@length**<br /><br /> **\@precision**<br /><br /> **\@Измените**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
  
## <a name="publication-properties-for-merge-replication"></a>Свойства публикации для репликации слиянием  
  
|Description|Хранимая процедура|Свойства|Требования|  
|-----------------|----------------------|----------------|------------------|  
|Изменение формата моментального снимка|**sp_changemergepublication**|**sync_mode**|Создание моментального снимка.|  
|Изменение расположения моментального снимка.|**sp_changemergepublication**|**alt_snapshot_folder**<br /><br /> **snapshot_in_defaultfolder**|Создание моментального снимка.|  
|Изменение расположения моментального снимка.|**sp_changedistpublisher, хранимая процедура**|**working_directory**|Создание моментального снимка.|  
|Изменение сжатия моментального снимка|**sp_changemergepublication**|**compress_snapshot**|Создание моментального снимка.|  
|Изменение любых параметров протокола FTP для моментального снимка|**sp_changemergepublication**|**enabled_for_internet**<br /><br /> **ftp_address**<br /><br /> **ftp_login**<br /><br /> **ftp_password**<br /><br /> **ftp_port**<br /><br /> **ftp_subdirectory**|Создание моментального снимка.|  
|Изменение скриптов, запускаемых перед моментальным снимком или после него.|**sp_changemergepublication**|**pre_snapshot_script**<br /><br /> **post_snapshot_script**|Создание моментального снимка (требуется также при изменении содержимого скрипта).<br /><br /> Для применения нового скрипта к подписчику требуется повторная инициализация.|  
|Добавление фильтра соединения или логической записи.|**sp_addmergefilter**|Все параметры.|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Удаление фильтра соединения или логической записи.|**sp_dropmergefilter**|Все параметры.|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение фильтра соединения или логической записи.|**sp_changemergefilter**|**\@свойства**<br /><br /> **\@значений**|Новый моментальный снимок<br /><br /> Повторная инициализация подписок.|  
|Отключение использования параметризованных фильтров (включение параметризованных фильтров не требует никаких специальных действий).|**sp_changemergepublication**|Значение **false** для **dynamic_filters**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Включение или выключение использования предварительно вычисляемых секций.|**sp_changemergepublication**|**use_partition_groups**|Создание моментального снимка.|  
|Включить или отключить [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] оптимизацию секций.|**sp_changemergepublication**|**keep_partition_changes**|Повторная инициализация подписок.|  
|Включение или выключение проверки секций подписчика.|**sp_changemergepublication**|**validate_subscriber_info**|Повторная инициализация подписок.|  
|Изменение уровня совместимости публикации до 80sp3 или ниже.|**sp_changemergepublication**|**publication_compatibility_level**|Создание моментального снимка.|  
  
## <a name="article-properties-for-merge-replication"></a>Свойства статьи для репликации слиянием  
  
|Description|Хранимая процедура|Свойства|Требования|  
|-----------------|----------------------|----------------|------------------|  
|Удаление статьи с последним параметризованным фильтром в публикации.|**sp_dropmergearticle**|Все параметры|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Удаление статьи, являющейся родителем в фильтре соединения или в логической записи (это побочный эффект удаления соединения).|**sp_dropmergearticle**|Все параметры|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Удаление статьи при прочих обстоятельствах.|**sp_dropmergearticle**|Все параметры|Создание моментального снимка.|  
|Включение в состав ранее не опубликованного фильтра столбцов.|**sp_mergearticlecolumn**|**\@рубрик**<br /><br /> **\@операцию**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Добавление, удаление или изменение фильтра строк.|**sp_changemergearticle**|**subset_filterclause**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.<br /><br /> Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.<br /><br /> Если статья не используется ни в каких фильтрах соединения, статью можно удалить и создать ее заново с другим фильтром строк, который не требует повторной инициализации всей подписки. Дополнительные сведения о добавлении и удалении статей см. в статье [Добавление и удаление статей в существующих публикациях](add-articles-to-and-drop-articles-from-existing-publications.md).|  
|Изменение параметров схемы.|**sp_changemergearticle**|**schema_option**|Создание моментального снимка.|  
|Изменение детализации отслеживания изменений от уровня столбцов до уровня строк (обратное изменение не требует дополнительных действий).|**sp_changemergearticle**|Значение **false** для **column_tracking**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Изменение режима, определяющего, будут ли проверяться разрешения до применения на издателе инструкций, созданных на подписчике.|**sp_changemergearticle**|**check_permissions**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
|Включение или выключение подписок, доступных только для загрузки (изменение других параметров отгрузки не требует каких-либо особых действий).|**sp_changemergearticle**|Изменение значения **subscriber_upload_options** на или с **2**|Повторная инициализация подписок.|  
|Изменение владельца целевой таблицы.|**sp_changemergearticle**|**destination_owner**|Создание моментального снимка.<br /><br /> Повторная инициализация подписок.|  
  
## <a name="see-also"></a>См. также:  
 [Вопросы и ответы об администрировании репликации](../administration/frequently-asked-questions-for-replication-administrators.md)   
 [Создание и применение моментального снимка](../create-and-apply-the-snapshot.md)   
 [Повторная инициализация подписок](../reinitialize-subscriptions.md)   
 [sp_addmergefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql)   
 [sp_articlecolumn &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)   
 [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql)   
 [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)   
 [sp_changearticlecolumndatatype &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql)   
 [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)   
 [sp_changemergefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql)   
 [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)   
 [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)   
 [sp_droparticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droparticle-transact-sql)   
 [sp_dropmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql)   
 [sp_dropmergefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql)   
 [sp_mergearticlecolumn &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql)  
  
  
