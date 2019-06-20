---
title: Разрешение проблем при обновлении | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 85de606ecea93aba80714d4266e9897dd856879f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66092501"
---
# <a name="resolving-upgrade-issues"></a>Разрешение проблем при обновлении
  В подразделах данного раздела содержатся описания проблем, которые могут быть выявлены, а также проблем, которые не могут быть выявлены, но которые могут повлиять на обновление или работу после обновления. Проблемы упорядочены по компонентам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Сведения о последних критических проблемах при обновлении](../../../2014/sql-server/install/late-breaking-upgrade-issues.md)  
  
-   [Проблемы обновления ядра СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
-   [Проблемы обновления полнотекстового поиска](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
-   [Проблемы репликации при обновлении](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
-   [Проблемы обновления служб Reporting Services &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
-   [Проблемы обновления агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
## <a name="issues-that-prevent-upgrading"></a>Проблемы, препятствующие обновлению  
 Некоторые настройки или параметры конфигурации предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут стать препятствием для обновления до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Если они обнаружены при установке [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], то процесс обновления будет остановлен и программа установки потребует запуска советника по переходу и устранения всех критических препятствий.  
  
### [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
 Если в отчете по обновлению компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] присутствуют перечисленные ниже задачи, то обновление до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] станет возможным только после того, как указанные действия будут выполнены.  
  
-   [Отсоедините базу данных с идентификатором 32767](../../../2014/sql-server/install/detach-database-id-32767.md)  
  
-   [Переименование имен для входа, которые совпадают с именами предопределенной роли сервера](../../../2014/sql-server/install/rename-logins-matching-fixed-server-role-names.md)  
  
-   [Переименуйте пользователя с именем sys](../../../2014/sql-server/install/rename-user-sys.md)  
  
-   [При помощи хранимой процедуры sp_rename переименуйте повторяющиеся имена индексов](../../../2014/sql-server/install/use-sp-rename-to-rename-duplicate-index-name.md)  
  
## <a name="see-also"></a>См. также  
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
