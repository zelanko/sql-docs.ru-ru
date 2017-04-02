---
title: "Управление службой Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "08/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "службы Integration Services, настройка"
  - "службы [службы Integration Services], настройка"
ms.assetid: 45554117-a0df-4830-b41c-5ebb33b764a5
caps.latest.revision: 63
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 63
---
# Управление службой Integration Services
    
> **ВАЖНО!** В данном разделе описывается компонент [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] — служба Windows для управления пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] поддерживает эту службу для обеспечения обратной совместимости с более ранними версиями служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], на сервере служб Integration Services можно управлять пакетами.  
  
 При установке компонента служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]также устанавливается служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . По умолчанию запускается служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и устанавливается ее автоматический запуск. Однако необходимо также установить среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , чтобы использовать эту службу для управления хранимыми и эксплуатируемыми пакетами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
> **ПРИМЕЧАНИЕ.** Для соединения непосредственно с экземпляром устаревшей версии службы Integration Service необходимо использовать версию SQL Server Management Studio (SSMS), соответствующую версии SQL Server, где выполняются службы Integration Services. Например, чтобы соединиться с устаревшей версией служб Integration Services, выполняющихся на экземпляре SQL Server 2016, необходимо использовать версию SSMS, выпущенную для SQL Server 2016. [Скачайте SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx).
>
>   В диалоговом окне SSMS **Соединение с сервером** нельзя вводить имя сервера, на котором работает более ранняя версия службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Однако чтобы управлять пакетами, которые хранятся на удаленном сервере, не нужно соединяться с экземпляром службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на этом удаленном сервере. Вместо этого измените файл конфигурации для службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] таким образом, чтобы среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] отображала пакеты, хранимые на удаленном сервере. Дополнительные сведения см. в разделе [Настройка служб Integration Services (SSIS)](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md).  
  
 Предусмотрена возможность установить только единственный экземпляр службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на отдельном компьютере. Эта служба не относится к конкретному экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Подключение к этой службе осуществляется с использованием имени компьютера, на котором она эксплуатируется.  
  
 Для управления службой [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] может применяться одна из следующих оснасток консоли управления (MMC): "Диспетчер конфигурации SQL Server" или "Службы". Прежде чем появится возможность управлять пакетами в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], необходимо убедиться, что служба запущена.  
  
 По умолчанию служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] настроена для управления пакетами в базе данных msdb экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], который установлен одновременно со службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Если экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] не установлен в то же время, служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] будет настроена для управления пакетами базы данных msdb локального экземпляра по умолчанию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Чтобы управлять пакетами, которые хранятся в именованном или удаленном экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]либо в нескольких экземплярах компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], необходимо изменить файл конфигурации для службы. Дополнительные сведения см. в разделе [Настройка служб Integration Services (SSIS)](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md).  
  
 По умолчанию служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] настроена таким образом, чтобы прекращать выполнение пакетов по завершении работы службы. Однако служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не ожидает прекращения выполнения пакетов, и некоторые пакеты могут продолжать выполняться по завершении работы службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Если работа службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] остановлена, можно продолжить выполнение пакетов с помощью мастера импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)], программы выполнения пакетов и программы командной строки **dtexec**(dtexec.exe). Однако контролировать выполнение пакетов невозможно.  
  
 По умолчанию служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] выполняется в контексте учетной записи NETWORK SERVICE.  
  
 Служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] вносит записи в журнал событий Windows. Также можно просмотреть события службы в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Можно также просматривать события службы с использованием программы просмотра событий.  
  
### Установка свойств службы Integration Services с помощью оснастки служб  
  
-   [задать свойства службы Integration Services](../../integration-services/service/set-the-properties-of-the-integration-services-service.md)  
  
### Просмотр событий службы, относящихся к службе Integration Services  
  
-   [просмотреть события службы Integration Services](../../integration-services/service/view-events-for-the-integration-services-service.md)  
  
## См. также  
 [Службы Integration Services (службы SSIS)](../../integration-services/service/integration-services-service-ssis-service.md)   
 [Настройка служб Integration Services (службы SSIS)](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md)   
 [мастер импорта и экспорта SQL Server](../Topic/SQL%20Server%20Import%20and%20Export%20Wizard.md)   
 [Программа dtexec](../../integration-services/packages/dtexec-utility.md)   
 [Запуск проектов и пакетов](https://msdn.microsoft.com/library/ms141708(v=sql.130).aspx)  
  
  