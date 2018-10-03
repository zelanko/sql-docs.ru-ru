---
title: Функции устаревшие Master Data Services в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: d8506bda-66dd-45a4-bfc9-3a10fa665acc
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 89d2d5d8cee989d6541cdb256b0a7aaf48d00162
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48142216"
---
# <a name="deprecated-master-data-services-features-in-sql-server-2014"></a>Устаревшие функции Master Data Services в SQL Server «2014»
  В этом разделе описаны устаревшие функции компонента [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , которые по-прежнему доступны в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Эти функции будут удалены в следующем выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Не следует использовать устаревшие функции в новых приложениях.  
  
## <a name="staging-process"></a>Промежуточный процесс  
 Промежуточный процесс, который использовался в [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] , более недоступен в веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ; но по-прежнему доступен в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 Промежуточные ошибки из промежуточного процесса [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] более не отображаются в пользовательском интерфейсе. Коды ошибок, выдаваемые в ходе промежуточного процесса по-прежнему доступны в промежуточных таблицах и можно найти здесь: [ http://msdn.microsoft.com/library/ff487022.aspx ](http://msdn.microsoft.com/library/ff487022.aspx).  
  
 Промежуточные таблицы (tblStgMember, tblStgMemberAttribute и tblStgRelationship) по-прежнему доступны в базе данных. Хранимая процедура, используемая для промежуточного процесса (mdm.udpStagingSweep), по-прежнему доступна в базе данных.  
  
 Методы веб-службы, которые вызывают промежуточный процесс, по-прежнему доступны.  
  
 Промежуточный интервал, заданный в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] , применим к промежуточному процессу как в [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] , так и [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 В [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]реализован новый, более производительный промежуточный процесс. Дополнительные сведения см. в разделе [Импорт данных (службы Master Data Services)](overview-importing-data-from-tables-master-data-services.md).  
  
## <a name="metadata"></a>Метаданные  
 Хотя модель «Метаданные» все еще отображается в веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , использовать ее не следует. В будущем выпуске она будет удалена. Теперь пользователи не могут просматривать метаданные в функциональной области **Обозреватель** и не могут создавать версии модели метаданных.  
  
## <a name="see-also"></a>См. также  
 [Неподдерживаемые функции служб Master Data Services в SQL Server 2014](discontinued-master-data-services-features.md)  
  
  
