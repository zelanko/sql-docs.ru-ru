---
title: Критические изменения в функциях средств управления в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 3ff3fad8-b569-4516-bd58-5a3efeb537e2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 73e2c6ecb4ae2f829c02897ed5c6ab5d84f1ba4b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62787022"
---
# <a name="breaking-changes-to-management-tools-features-in-sql-server-2014"></a>Критические изменения в функциях средств управления в SQL Server 2014
  В этом разделе описаны критические изменения в функциях средств управления. Эти изменения могут нарушать работу приложений, скриптов или механизмов, основанных на более ранних версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При обновлении могут возникнуть следующие проблемы. Дополнительные сведения см. в разделе [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
## <a name="breaking-changes-in-sssql14"></a>Критические изменения в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Сведения будут доступны позже.  
  
## <a name="breaking-changes-in-sssql11"></a>Критические изменения в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="you-cannot-use-sssql11-management-tools-to-create-a-utility-control-point-on-a-sskilimanjaro-instance-of-sql-server"></a>Средства управления [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] нельзя использовать для создания точки управления служебной программой в экземпляре SQL Server [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] .  
 Для создания точки управления служебной программой в экземпляре [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]используйте средства управления [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] .  
  
### <a name="smo-has-been-reversioned-in-sssql11"></a>В [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] изменилась версия объектов SMO.  
 Код, использующий объекты SMO из [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] или более ранних версий, может оказаться неработоспособным в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] без внесения небольших изменений. Дополнительные сведения см. в разделе [Backward Compatibility in SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md).  

## <a name="breaking-changes-in-sql-server-2005"></a><a name="previous-versions"></a>Критические изменения в SQL Server 2005  

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a>См. также  
 [Обратная совместимость](../../2014/getting-started/backward-compatibility.md)  
 [Дополнительные сведения о критических изменениях в функциях средств управления в SQL Server 2014](breaking-changes-to-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)  
  
  
