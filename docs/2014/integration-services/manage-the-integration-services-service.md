---
title: Управление службой Integration Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- services [Integration Services], configuring
ms.assetid: 45554117-a0df-4830-b41c-5ebb33b764a5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fc3b1eb4e73b3d77b49cc9f485e0a6fc456a8875
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66057793"
---
# <a name="manage-the-integration-services-service"></a>Управление службой Integration Services
    
> [!IMPORTANT]  
>  В данном разделе описывается компонент [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] — служба Windows для управления пакетами служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] поддерживает эту службу для обеспечения обратной совместимости с более ранними версиями служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Начиная с [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], на сервере служб Integration Services можно управлять пакетами.  
  
 При установке компонента служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]также устанавливается служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . По умолчанию запускается служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и устанавливается ее автоматический запуск. Однако необходимо также установить среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , чтобы использовать эту службу для управления хранимыми и эксплуатируемыми пакетами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
> [!NOTE]  
>  Нельзя подключиться к экземпляру [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] службы из [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] версии. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] То есть, в диалоговом окне **Соединение с сервером** нельзя вводить имя сервера, на котором работает только служба [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] версии [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Однако можно изменить файл конфигурации для этой службы и тем самым обеспечить управление пакетами, хранящимися на экземпляре [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] , из среды [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] версии [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Дополнительные сведения см. в разделе [Настройка служб Integration Services (службы SSIS)](service/integration-services-service-ssis-service.md).  
  
 Предусмотрена возможность установить только единственный экземпляр службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на отдельном компьютере. Эта служба не относится к конкретному экземпляру компонента [!INCLUDE[ssDE](../includes/ssde-md.md)]. Подключение к этой службе осуществляется с использованием имени компьютера, на котором она эксплуатируется.  
  
 Для управления службой [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] может применяться одна из следующих оснасток консоли управления (MMC): "Диспетчер конфигурации SQL Server" или "Службы". Прежде чем появится возможность управлять пакетами в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], необходимо убедиться, что служба запущена.  
  
 По умолчанию служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] настроена для управления пакетами в базе данных msdb экземпляра компонента [!INCLUDE[ssDE](../includes/ssde-md.md)], который установлен одновременно со службами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Если экземпляр компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] не установлен в то же время, служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] будет настроена для управления пакетами базы данных msdb локального экземпляра по умолчанию компонента [!INCLUDE[ssDE](../includes/ssde-md.md)]. Чтобы управлять пакетами, которые хранятся в именованном или удаленном экземпляре компонента [!INCLUDE[ssDE](../includes/ssde-md.md)]либо в нескольких экземплярах компонента [!INCLUDE[ssDE](../includes/ssde-md.md)], необходимо изменить файл конфигурации для службы. Дополнительные сведения см. в разделе [Настройка служб Integration Services (службы SSIS)](service/integration-services-service-ssis-service.md).  
  
 По умолчанию служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] настроена таким образом, чтобы прекращать выполнение пакетов по завершении работы службы. Однако служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] не ожидает прекращения выполнения пакетов, и некоторые пакеты могут продолжать выполняться по завершении работы службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Если работа службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] остановлена, можно продолжить выполнение пакетов с помощью мастера импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] , программы выполнения пакетов и программы командной строки **dtexec** (dtexec.exe). Однако контролировать выполнение пакетов невозможно.  
  
 По умолчанию служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] выполняется в контексте учетной записи NETWORK SERVICE.  
  
 Служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] вносит записи в журнал событий Windows. Также можно просмотреть события службы в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Можно также просматривать события службы с использованием программы просмотра событий.  
  
### <a name="to-set-properties-of-integration-services-service-using-the-services-snap-in"></a>Установка свойств службы Integration Services с помощью оснастки служб  
  
-   [задать свойства службы Integration Services](../../2014/integration-services/set-the-properties-of-the-integration-services-service.md)  
  
### <a name="to-view-service-events-for-integration-services-service"></a>Просмотр событий службы, относящихся к службе Integration Services  
  
-   [просмотреть события службы Integration Services](../../2014/integration-services/view-events-for-the-integration-services-service.md)  
  
## <a name="see-also"></a>См. также  
 [Служба Integration Services служб SSIS &#40;&#41;](service/integration-services-service-ssis-service.md)   
 [Настройка службы Integration Services &#40;служб SSIS&#41;](configuring-the-integration-services-service-ssis-service.md)   
 [Мастер импорта и экспорта SQL Server](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)   
 [Программа dtexec](packages/dtexec-utility.md)   
 [Запуск проектов и пакетов](packages/run-integration-services-ssis-packages.md)  
  
  
