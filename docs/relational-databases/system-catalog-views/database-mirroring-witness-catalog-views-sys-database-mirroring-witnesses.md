---
title: sys.database_mirroring_witnesses (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.database_mirroring_witnesses
- sys.database_mirroring_witnesses_TSQL
- database_mirroring_witnesses
- database_mirroring_witnesses_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], catalog views
- sys.database_mirroring_witnesses catalog view
- witness [SQL Server], sys.database_mirroring_witnesses catalog view
ms.assetid: 0dd5b794-733b-4a3c-b5a4-62f9f1f0f22d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 52a56f07422da3dc0bf78a4560f9f6573000050f
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031332"
---
# <a name="database-mirroring-witness-catalog-views---sysdatabasemirroringwitnesses"></a>Представления каталога свидетеля зеркального отображения - базы данных sys.database_mirroring_witnesses
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой из следящих ролей, исполняемых сервером при участии в зеркальном отображении базы данных. 
  
  При зеркальном отображении базы данных для автоматической отработки отказа требуется следящий сервер. Желательно, чтобы следящий сервер находился на компьютере, отдельном от основного и зеркального серверов. Следящий сервер не обслуживает базу данных, а производит мониторинг состояния основного и зеркального серверов. Если основной сервер дает сбой, следящий сервер может инициировать автоматический переход на зеркальный сервер. 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_name**|**sysname**|Имя двух копий базы данных в сеансе зеркального отображения базы данных.|  
|**principal_server_name**|**sysname**|Имя сервера-участника, копия базы данных которого в настоящее время является основной базой данных.|  
|**mirror_server_name**|**sysname**|Имя сервера-участника, копия базы данных которого в настоящее время является зеркальной базой данных.|  
|**safety_level**|**tinyint**|Уровень безопасности транзакции для выполнения изменений в зеркальной базе данных.<br /><br /> 0 = неизвестное состояние.<br /><br /> 1 = выключен (асинхронно).<br /><br /> 2 = полный (синхронно).<br /><br /> Использование слежения для автоматической отработки отказа требует полного уровня безопасности, который включен по умолчанию.|  
|**safety_level_desc**|**nvarchar(60)**|Описание гарантий безопасности изменений в зеркальной базе данных.<br /><br /> UNKNOWN<br /><br /> OFF<br /><br /> FULL|  
|**safety_sequence_number**|**int**|Последовательный номер обновления для изменения **safety_level**.|  
|**role_sequence_number**|**int**|Последовательный номер обновления для переключения ролей главного и зеркального сервера, исполняемых каждым из участников зеркального отображения.|  
|**mirroring_guid**|**uniqueidentifier**|Идентификатор участия зеркального отображения.|  
|**family_guid**|**uniqueidentifier**|Идентификатор семейства для резервирования базы данных. Используется для выявления совпадающих состояний восстановления.|  
|**is_suspended**|**bit**|Зеркальное отображение базы данных приостановлено.|  
|**is_suspended_sequence_number**|**int**|Порядковый номер параметра **is_suspended**.|  
|**partner_sync_state**|**tinyint**|Состояние синхронизации сеанса зеркального отображения базы данных:<br /><br /> 5 = участники синхронизированы. Отработка отказа возможна. Сведения о требованиях к отработке отказа см.в [переключение ролей во время база данных зеркального отображения сеанса &#40;SQL Server&#41;](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md).<br /><br /> 6 = участники не синхронизированы. Отработка отказа сейчас невозможна;|  
|**partner_sync_state_desc**|**nvarchar(60)**|Описание состояния синхронизации сеанса зеркального отображения:<br /><br /> SYNCHRONIZED<br /><br /> UNSYNCHRONIZED|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Следящий сервер зеркального отображения базы данных](../../database-engine/database-mirroring/database-mirroring-witness.md)   
 [sys.database_mirroring &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md)   
 [sys.database_mirroring_endpoints (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
