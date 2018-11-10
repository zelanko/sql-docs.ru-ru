---
title: Обновление служб Analysis Services | Документы Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- databases [Analysis Services], upgrading
- installing Analysis Services, side-by-side installations
- Analysis Services upgrades
- Analysis Services upgrades, about upgrading Analysis Services
- SSAS, database migration
- upgrading Analysis Services
- installing Analysis Services, upgrading
- SSAS, upgrading
ms.assetid: a131d329-386e-4470-aaa9-ffcde4e5ec0c
author: Minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 88dfe4836cc84b7792639817a01c026f6d3f3283
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018109"
---
# <a name="upgrade-analysis-services"></a>Обновление служб Analysis Services
  Используйте пакет установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Подробные сведения об обновлении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме интеграции с SharePoint см. в разделе [обновление PowerPivot для SharePoint](upgrade-power-pivot-for-sharepoint.md). Дополнительные сведения об обновлении существующего SQL Server экземпляра, см. в разделе [обновление до SQL Server 2014 с помощью мастера установки &#40;установки&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md).  
  
## <a name="known-upgrade-issues"></a>Известные проблемы при обновлении  
 Перед обновлением до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]просмотрите следующие источники:  
  
-   [Заметки о выпуске SQL Server 2014](http://go.microsoft.com/fwlink/?LinkID=296445).  
  
-   Сведения о [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] функции и возможности не поддерживаются, устарели или изменить см. в разделе [обратная совместимость служб Analysis Services](../../analysis-services/analysis-services-backward-compatibility.md).  
  
## <a name="pre-upgrade-checklist"></a>Контрольный список действий перед обновлением  
 Перед обновлением просмотрите следующую информацию:  
  
-   [Поддерживаемые обновления версий и выпусков](supported-version-and-edition-upgrades.md)  
  
-   [Требования к оборудованию и программному обеспечению для установки SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [Параметры для средства проверки конфигурации системы](check-parameters-for-the-system-configuration-checker.md)  
  
-   [Вопросы безопасности при установке SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
-   [Создание и восстановление резервных копий баз данных служб Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
-   [Использование помощника по обновлению для подготовки к обновлениям](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
## <a name="upgrading-analysis-services"></a>Обновление служб Analysis Services  
 Можно выбрать один из нескольких способов обновления сервера и данных.  
  
-   **Обновление на месте** заменяет существующие файлы программы с [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] программные файлы. Базы данных остаются в том же расположении. Программные папки обновляются с целью отражения нового имени.  
  
-   Объект **обновление side-by-side** является новой установкой [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] на том же компьютере, который имеет существующий экземпляр служб Analysis Services. Можно перенести базы данных на новый экземпляр на этом же компьютере и затем удалить старую версию, если она больше не используется.  
  
-   Можно также установить службы Analysis Services на новом оборудовании, а затем осуществить миграцию существующих баз данных на этот сервер.  
  
## <a name="in-place-upgrade"></a>Обновление на месте  
 Можно выполнить обновление версии существующего экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and, as part of the upgrade process, auдоmatically migrate existing databases from the old instance до the new instance. Поскольку метаданные и двоичные данные между двумя версиями совместимы, после обновления данные сохраняются и их не нужно переносить вручную.  
  
 Чтобы обновить существующий экземпляр, запустите программу установки и укажите имя существующего экземпляра в качестве имени нового экземпляра.  
  
## <a name="upgrading-databases"></a>Обновление баз данных  
 Базы данных, созданные в предыдущих версиях служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , на обновленном сервере работают со старым значением уровня совместимости. Базы данных, созданные в следующих версиях, имеют уровень совместимости баз данных 105. Если необходимо использовать функции, требующие нового уровня совместимости базы данных, уровень совместимости можно изменить. В противном случае базы данных можно запустить на обновленном сервере, используя исходные параметры. Дополнительные сведения см. в разделе [установить уровень совместимости многомерной базы данных &#40;служб Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md).  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функции, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Основные сведения об архитектуре Microsoft OLAP](../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)   
 [Обновление PowerPivot для SharePoint](upgrade-power-pivot-for-sharepoint.md)   
 [Установка служб Analysis Services в многомерном режиме и режиме интеллектуального анализа данных](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md)   
 [Установка PowerPivot для SharePoint 2010](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
