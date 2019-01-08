---
title: Службы Integration Services (службы SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, about Integration Services service
- SQL Server Integration Services service
- service [Integration Services],about Integration Services service
- service [Integration Services]
- SQL Server Integration Services, service
ms.assetid: 2c785b3b-4a0c-4df7-b5cd-23756dc87842
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cfbbf84cf084ae96e123c14e659ebeb30c12ac42
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52800776"
---
# <a name="integration-services-service-ssis-service"></a>Службы Integration Services (службы SSIS)
  В подразделах этого раздела описывается служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] — служба Windows для управления пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Эта служба не требуется для создания, сохранения и выполнения пакетов служб Integration Services. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] поддерживает службу [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для обеспечения обратной совместимости с более ранними версиями служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] сохраняют объекты, настройки и рабочие данные в `SSISDB` базу данных для проектов, которые вы развернули в [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] сервера с помощью модели развертывания проекта. На сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , который является экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ядра СУБД, размещается база данных. Дополнительные сведения о базе данных см. в разделе [Каталог служб SSIS](../catalog/ssis-catalog.md). Дополнительные сведения о развертывании проектов на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в разделе [Развертывание проектов на сервере служб Integration Services](../deploy-projects-to-integration-services-server.md).  
  
## <a name="management-capabilities"></a>Функции управления  
 Служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] является службой Windows для управления пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] доступна только в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Использование службы Windows служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] дает следующие возможности управления:  
  
-   запуск удаленных и локально хранимых пакетов;  
  
-   остановка удаленных и локально запущенных пакетов;  
  
-   наблюдение за работой удаленных и локальных пакетов;  
  
-   импорт и экспорт пакетов;  
  
-   управление хранилищем пакетов;  
  
-   настройка папок хранения;  
  
-   остановка запущенных пакетов при остановке службы;  
  
-   просмотр журнала событий Windows;  
  
-   соединение с несколькими серверами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
## <a name="startup-type-for-integration-services-service"></a>Тип запуска службы Integration Services  
 Служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] устанавливается при установке компонента [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию запускается служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и устанавливается ее автоматический запуск. Для наблюдения за пакетами, хранящимися в хранилище пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , эта служба должна быть запущена. Хранилищем пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] может быть как база данных msdb в экземпляре служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и назначенные папки файловой системы.  
  
 Запуск службы Windows служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не требуется, если необходимо только создавать и выполнять пакеты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Однако эта служба необходима для перечисления и монитора пакетов, использующих среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [задать свойства службы Integration Services](../set-the-properties-of-the-integration-services-service.md)  
  
-   [Просмотр событий службы Integration Services](../view-events-for-the-integration-services-service.md)  
  
  
