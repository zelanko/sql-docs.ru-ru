---
title: "Страница \"Конфигурация базы данных\" (диспетчер конфигурации служб Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.mds.configmanager.dbpg.f1
ms.assetid: dd72220e-a599-465d-8b84-9bb6a7433216
caps.latest.revision: "8"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bdbdbafcfc2981633b1965492addea21dbb7ad7c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="database-configuration-page-master-data-services-configuration-manager"></a>Страница «Конфигурация базы данных» (диспетчер конфигурации служб Master Data Services)
  Страница **Настройка база данных** служит для изменения системных настроек базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Системные настройки влияют на все веб-приложения и веб-службы, связанные с выбранной базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Чтобы системные настройки стали доступными для изменения, необходимо выбрать или создать базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
## <a name="current-database"></a>Текущая база данных  
 Выберите существующую базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] или создайте новую, для которой будут редактироваться системные настройки. Новая база данных будет выбрана по умолчанию после ее создания.  
  
|Имя элемента управления|Description|  
|------------------|-----------------|  
|**Экземпляр SQL Server**|Отображает имя выбранного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Не содержит значения до подключения к экземпляру и выбора или создания базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**База данных служб основных данных**|Отображает имя выбранной базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Не содержит значения до подключения к экземпляру и выбора или создания базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Версия базы данных Master Data Services**|Версия схемы базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Создание базы данных**|Открывает **мастер создания базы данных** для соединения с экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и создания базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] на этом экземпляре.|  
|**Выбор базы данных**|Откройте диалоговое окно **Подключение к базе данных** для подключения к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и выбора базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Обновление базы данных**|Открывает мастер, с помощью которого можно обновить указанную базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Эта кнопка включена только в тех случаях, когда требуется обновление определенной базы данных.|  
|**Исправление базы данных**|Эта кнопка позволяет убедиться в правильности установки базы данных MDS. Эта возможность может оказаться полезной при создании и восстановлении резервной копии базы данных MDS на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , где база данных MDS ранее не размещалась.|  
  
## <a name="system-settings"></a>Системные настройки  
 Изменение системных параметров для всех веб-приложений и веб-служб, связанных с выбранной базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 Эти параметры доступны в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] и хранятся в таблице системных параметров (mdm.tblSystemSetting) базы данных. Список параметров см. в разделе [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>См. также:  
[Установка и настройка служб Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md) [Требования к базе данных (службы Master Data Services)](../master-data-services/install-windows/database-requirements-master-data-services.md)  
  
  
