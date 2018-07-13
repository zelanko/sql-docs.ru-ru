---
title: Критические изменения в управления возможности средств в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3ff3fad8-b569-4516-bd58-5a3efeb537e2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f206da123659c750f955d2132142dcae76df6a46
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165355"
---
# <a name="breaking-changes-to-management-tools-features-in-sql-server-2014"></a>Критические изменения в функциях средств управления в SQL Server 2014
  В этом разделе описаны критические изменения в функциях средств управления. Эти изменения могут нарушать работу приложений, скриптов или механизмов, основанных на более ранних версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При обновлении могут возникнуть следующие проблемы. Дополнительные сведения см. в разделе [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
## <a name="breaking-changes-in-includesssql14includessssql14-mdmd"></a>Критические изменения в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Сведения будут доступны позже.  
  
## <a name="breaking-changes-in-includesssql11includessssql11-mdmd"></a>Критические изменения в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="you-cannot-use-includesssql11includessssql11-mdmd-management-tools-to-create-a-utility-control-point-on-a-includesskilimanjaroincludessskilimanjaro-mdmd-instance-of-sql-server"></a>Средства управления [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] нельзя использовать для создания точки управления служебной программой в экземпляре SQL Server [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] .  
 Для создания точки управления служебной программой в экземпляре [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]используйте средства управления [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] .  
  
### <a name="smo-has-been-reversioned-in-includesssql11includessssql11-mdmd"></a>SMO изменилась версия в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 Код, использующий объекты SMO из [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] или более ранних версий, может оказаться неработоспособным в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] без внесения небольших изменений. Дополнительные сведения см. в разделе [Backward Compatibility in SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md).  
  
## <a name="see-also"></a>См. также  
 [Обратная совместимость](../../2014/getting-started/backward-compatibility.md)  
  
  
