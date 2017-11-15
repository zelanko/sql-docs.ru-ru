---
title: "Требования к базе данных (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe731839-c5c4-4884-bb6a-644eca28bb30
caps.latest.revision: "18"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f161508759830d515f946cc4f4e06088dfde08de
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="database-requirements-master-data-services"></a>Требования к базе данных (службы Master Data Services)
  Все основные данные хранятся в базе данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . На сервере, на котором размещена эта база данных, должен быть запущен экземпляр компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Воспользуйтесь средством [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] для создания и настройки базы данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] на локальном или удаленном компьютере. Если база данных перемещается из одной среды в другую, то можно сохранить информацию в новой среде, связав веб-службу [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] и [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] с базой данных в новом расположении.  
  
> [!NOTE]  
>  Любой компьютер, на котором устанавливаются компоненты [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , должен иметь соответствующие лицензии. Дополнительные сведения см. в лицензионном соглашении.  
  
## <a name="requirements"></a>Требования  
 Перед началом создания базы данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] проверьте выполнение следующих требований.  
  
### <a name="sql-server-edition"></a>Выпуск SQL Server  
 База данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] может быть размещена на следующих выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
 
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] Enterprise x64 (64-разрядная версия)  
  
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] Developer Edition x64 (64-разрядная версия)  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence x64 (64-разрядная версия)  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise x64 (64-разрядная версия)  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer Edition x64 (64-разрядная версия)  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Business Intelligence x64 (64-разрядная версия)  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Enterprise (64-разрядная версия) x64 — обновление только с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Developer Edition x64 (64-разрядная версия)  
  
-   64-разрядная версия Microsoft SQL Server 2008 R2 Enterprise x64  
  
-   Microsoft SQL Server 2008 R2 Developer x64 (64-разрядная версия)  
  
 Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md). 
  
### <a name="operating-system"></a>Операционная система  
 Дополнительные сведения о поддерживаемых операционных системах Windows и других требованиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] см. в статье [Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
### <a name="accounts-and-permissions"></a>Учетные записи и разрешения  
  
|Тип|Описание|  
|----------|-----------------|  
|Учетная запись пользователя|В [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]для соединения с экземпляром компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , на котором размещена база данных служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , можно использовать учетную запись Windows или учетную запись [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Учетная запись пользователя должна принадлежать роли сервера **sysadmin** на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Дополнительные сведения о роли **sysadmin** см. в статье [Роли уровня сервера](../../relational-databases/security/authentication-access/server-level-roles.md).|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] учетная запись администратора|При создании базы данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] необходимо указать учетную запись пользователя домена, который является системным администратором [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Для всех веб-приложений [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], связанных с этой базой данных, пользователь может обновлять все модели и все данные во всех функциональных областях. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../../master-data-services/administrators-master-data-services.md).|  
  
### <a name="database-backup"></a>Резервное копирование базы данных  
 Рекомендуется выполнять резервное копирование базы данных ежедневно в периоды низкой активности, а резервные копии журнала транзакций следует делать чаще в соответствии с требованиями среды. Дополнительные сведения о резервных копиях см. в статье [Общие сведения о резервном копировании (SQL Server)](../../relational-databases/backup-restore/backup-overview-sql-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)   
 [Создание базы данных служб Master Data Services](../../master-data-services/install-windows/create-a-master-data-services-database.md)   
 [База данных служб Master Data Services](../../master-data-services/master-data-services-database.md)   
 [Диалоговое окно "Подключение к базе данных служб Master Data Services"](../../master-data-services/connect-to-a-master-data-services-database-dialog-box.md)   
 [Мастер создания базы данных (диспетчер конфигурации служб Master Data Services)](../../master-data-services/create-database-wizard-master-data-services-configuration-manager.md)  
  
  
