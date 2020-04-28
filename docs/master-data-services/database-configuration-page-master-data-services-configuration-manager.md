---
title: Страница «Конфигурация базы данных»
ms.custom: seo-lt-2019
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql13.mds.configmanager.dbpg.f1
ms.assetid: dd72220e-a599-465d-8b84-9bb6a7433216
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 82b3762342c30b657f031bd53f89ae7652f5ece8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "73729434"
---
# <a name="database-configuration-page-master-data-services-configuration-manager"></a>Страница «Конфигурация базы данных» (диспетчер конфигурации служб Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Страница **Настройка база данных** служит для изменения системных настроек базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Системные настройки влияют на все веб-приложения и веб-службы, связанные с выбранной базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Чтобы системные настройки стали доступными для изменения, необходимо выбрать или создать базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
## <a name="current-database"></a>Текущая база данных  
 Выберите существующую базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] или создайте новую, для которой будут редактироваться системные настройки. Новая база данных будет выбрана по умолчанию после ее создания.  
  
|Имя элемента управления|Описание|  
|------------------|-----------------|  
|**Экземпляр SQL Server**|Отображает имя выбранного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Не содержит значения до подключения к экземпляру и выбора или создания базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**База данных Master Data Services**|Отображает имя выбранной базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Не содержит значения до подключения к экземпляру и выбора или создания базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
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
  
  
