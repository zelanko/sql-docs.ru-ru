---
title: Разрешение проблем при обновлении | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6072fb3c1d52048832bd6d07f34828c84eb2d491
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101212"
---
# <a name="resolving-upgrade-issues"></a>Разрешение проблем при обновлении
  В подразделах данного раздела содержатся описания проблем, которые могут быть выявлены, а также проблем, которые не могут быть выявлены, но которые могут повлиять на обновление или работу после обновления. Проблемы упорядочены по компонентам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Последние сведения о проблемах обновления](../../../2014/sql-server/install/late-breaking-upgrade-issues.md)  
  
-   [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
-   [Проблемы обновления компонента Full-Text Search](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
-   [Проблемы обновления репликации](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
-   [Проблемы обновления служб Reporting Services &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
-   [Проблемы обновления агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
## <a name="issues-that-prevent-upgrading"></a>Проблемы, препятствующие обновлению  
 Некоторые настройки или параметры конфигурации предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут стать препятствием для обновления до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Если они обнаружены при установке [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], то процесс обновления будет остановлен и программа установки потребует запуска советника по переходу и устранения всех критических препятствий.  
  
### [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
 Если в отчете по обновлению компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] присутствуют перечисленные ниже задачи, то обновление до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] станет возможным только после того, как указанные действия будут выполнены.  
  
-   [Отсоедините базу данных с Идентификатором 32767](../../../2014/sql-server/install/detach-database-id-32767.md)  
  
-   [Переименовать имена входа, совпадающие имена предопределенных ролей сервера](../../../2014/sql-server/install/rename-logins-matching-fixed-server-role-names.md)  
  
-   [Переименуйте пользователя с именем sys](../../../2014/sql-server/install/rename-user-sys.md)  
  
-   [С помощью хранимой процедуры sp_rename переименуйте повторяющиеся имена индексов](../../../2014/sql-server/install/use-sp-rename-to-rename-duplicate-index-name.md)  
  
## <a name="see-also"></a>См. также  
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
