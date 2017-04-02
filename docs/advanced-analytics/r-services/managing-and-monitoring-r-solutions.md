---
title: "Мониторинг решений R и управление ими | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d455f22a-190f-4a28-9088-98a843cd5db2
caps.latest.revision: 15
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# Мониторинг решений R и управление ими
  Администраторам баз данных необходимо интегрировать конкурирующие проекты и приоритеты в единую точку контакта: сервер базы данных. Им необходимо предоставить доступ к данным не только специалистам по анализу, но и различным разработчикам отчетов, бизнес-аналитикам и потребителям бизнес-данных, поддерживая при этом работоспособность операционного хранилища данных и хранилища отчетов. На предприятии администратор базы данных — это важная часть процесса построения и развертывания эффективной инфраструктуры для обработки и анализа данных. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] предоставляют администратору базы данных, который поддерживает роль обработки и анализа данных, множество преимуществ.  
  
-   **Безопасность.** Архитектура [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] защищает ваши базы данных и изолирует выполнение сеансов R от экземпляра базы данных.  
  
     Можно указать, кто может выполнять сценарии R, чтобы данные, используемые в заданиях R, контролировались ролями безопасности, определенными в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Надежность.** Сеансы R выполняются в отдельном процессе, чтобы сервер продолжал работать как обычно даже при возникновении проблем в сеансе R. Недостаточно привилегий физических учетных записей используются для содержания и выделить R экземпляры.   
  
-   **Управление ресурсами.** Можно управлять объемом ресурсов, выделяемых для среды выполнения R, чтобы предотвратить негативное влияние масштабных вычислений на общую производительность сервера.  
  
  
## В этом разделе  
 [Наблюдение за службами R](../../advanced-analytics/r-services/monitoring-r-services.md)
 
 [Управление ресурсами для служб R](../../advanced-analytics/r-services/resource-governance-for-r-services.md)
 
[Установка и управление пакетами R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md)
  
[Конфигурация](../../advanced-analytics/r-services/configuration-sql-server-r-services.md) 

+ [Настройка и управление расширениями углубленной аналитики](../../advanced-analytics/r-services/configure-and-manage-advanced-analytics-extensions.md)  
  
+  [Изменение пула учетных записей пользователей для служб SQL Server R](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md)  

 [Вопросы безопасности для среды выполнения R в SQL Server](../../advanced-analytics/r-services/security-considerations-for-the-r-runtime-in-sql-server.md)  
  
 
  
## См. также:  
 [Возможности и задачи служб R SQL Server](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)  
  
  