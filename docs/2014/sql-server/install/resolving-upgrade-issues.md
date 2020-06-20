---
title: Устранение проблем с обновлением | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Upgrade Advisor [SQL Server], reference
- component issue resolution [Upgrade Advisor]
- resolving upgrade issues
- upgrade blocks [Upgrade Advisor]
- detecting upgrade issues
- finding upgrade issues
- Upgrade Advisor [SQL Server], blocking issues
- configurations preventing upgrading [Upgrade Advisor]
- locating upgrade issues
- blocking issues [Upgrade Advisor]
- issues preventing upgrading [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, reference
- analyzing system [Upgrade Advisor], resolving issues
- settings preventing upgrading [Upgrade Advisor]
- upgrade issue reference [Upgrade Advisor]
- identifying upgrade issues
- fixing upgrade issues [Upgrade Advisor]
ms.assetid: 113eb435-8d36-4ed6-9790-b5e4c14809c8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c00b08d40bc8c17013e6af19b5d11b0b7ad78c4b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058993"
---
# <a name="resolving-upgrade-issues"></a>Разрешение проблем при обновлении
  В подразделах данного раздела содержатся описания проблем, которые могут быть выявлены, а также проблем, которые не могут быть выявлены, но которые могут повлиять на обновление или работу после обновления. Проблемы упорядочены по компонентам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Сведения о последних критических проблемах при обновлении](../../../2014/sql-server/install/late-breaking-upgrade-issues.md)  
  
-   [Проблемы обновления ядра СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
-   [Проблемы обновления полнотекстового поиска](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
-   [Проблемы репликации при обновлении](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
-   [Reporting Services проблем обновления &#40;советник по переходу&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
-   [Проблемы обновления агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
## <a name="issues-that-prevent-upgrading"></a>Проблемы, препятствующие обновлению  
 Некоторые настройки или параметры конфигурации предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут стать препятствием для обновления до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Если они обнаружены при установке [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], то процесс обновления будет остановлен и программа установки потребует запуска советника по переходу и устранения всех критических препятствий.  
  
### [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
 Если в отчете по обновлению компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] присутствуют перечисленные ниже задачи, то обновление до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] станет возможным только после того, как указанные действия будут выполнены.  
  
-   [Отсоедините базу данных с идентификатором 32767](../../../2014/sql-server/install/detach-database-id-32767.md)  
  
-   [Переименование имен для входа, которые совпадают с именами предопределенной роли сервера](../../../2014/sql-server/install/rename-logins-matching-fixed-server-role-names.md)  
  
-   [Переименуйте пользователя с именем sys](../../../2014/sql-server/install/rename-user-sys.md)  
  
-   [При помощи хранимой процедуры sp_rename переименуйте повторяющиеся имена индексов](../../../2014/sql-server/install/use-sp-rename-to-rename-duplicate-index-name.md)  
  
## <a name="see-also"></a>См. также:  
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
