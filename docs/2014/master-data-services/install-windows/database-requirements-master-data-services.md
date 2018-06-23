---
title: Требования к базе данных (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe731839-c5c4-4884-bb6a-644eca28bb30
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 09fed573dfeda16bdefc1c1f92536a37ce6bd902
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190018"
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
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence x64 (64-разрядная версия)  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise x64 (64-разрядная версия)  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer Edition x64 (64-разрядная версия)  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Business Intelligence x64 (64-разрядная версия)  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Enterprise (64-разрядная версия) x64 — обновление только с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Developer Edition x64 (64-разрядная версия)  
  
-   64-разрядная версия Microsoft SQL Server 2008 R2 Enterprise x64  
  
-   Microsoft SQL Server 2008 R2 Developer x64 (64-разрядная версия)  
  
 Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
### <a name="operating-system"></a>Операционная система  
 Дополнительные сведения о поддерживаемых операционных системах Windows и другие требования для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)], в разделе [оборудованию и программному обеспечению для установки SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
### <a name="accounts-and-permissions"></a>Учетные записи и разрешения  
  
|Тип|Описание|  
|----------|-----------------|  
|Учетная запись пользователя|В [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]для соединения с экземпляром компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , на котором размещена база данных служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , можно использовать учетную запись Windows или учетную запись [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Учетная запись пользователя должна принадлежать роли сервера **sysadmin** на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Дополнительные сведения о роли **sysadmin** см. в статье [Роли уровня сервера](../../relational-databases/security/authentication-access/server-level-roles.md).|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] учетная запись администратора|При создании базы данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] необходимо указать учетную запись пользователя домена, который является системным администратором [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Для всех веб-приложений [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], связанных с этой базой данных, пользователь может обновлять все модели и все данные во всех функциональных областях. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).|  
  
### <a name="database-backup"></a>Резервное копирование базы данных  
 Рекомендуется выполнять резервное копирование базы данных ежедневно в периоды низкой активности, а резервные копии журнала транзакций следует делать чаще в соответствии с требованиями среды. Дополнительные сведения о резервных копиях см. в статье [Общие сведения о резервном копировании (SQL Server)](../../relational-databases/backup-restore/backup-overview-sql-server.md).  
  
## <a name="see-also"></a>См. также  
 [Установка служб Master Data Services](install-master-data-services.md)   
 [Создание базы данных служб Master Data Services](create-a-master-data-services-database.md)   
 [База данных служб Master Data Services](../master-data-services-database.md)   
 [Диалоговое окно "Подключение к базе данных служб Master Data Services"](../connect-to-a-master-data-services-database-dialog-box.md)   
 [Мастер создания базы данных (диспетчер конфигурации служб Master Data Services)](../create-database-wizard-master-data-services-configuration-manager.md)  
  
  