---
title: "Завершение обновления ядра СУБД | Microsoft Docs"
ms.custom: ""
ms.date: "09/22/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f08087e-e532-416c-8caa-e0ec88c57596
caps.latest.revision: 10
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 10
---
# Завершение обновления ядра СУБД
  После завершения обновления до SQL Server 2016 вам, возможно, потребуется выполнить некоторые дополнительные действия. следующие основные параметры.  
  
 После обновления компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] выполните следующие действия.  
  
-   **Резервное копирование баз данных:** создайте полную резервную копию каждой обновленной базы данных.  
  
-   **Включение новых функций:** в SQL Server 2016 некоторые изменения включаются только после того, как уровень совместимости базы данных DATABASE_COMPATIBILITY изменится на 130.  Дополнительные сведения и рекомендуемый рабочий процесс см. в разделе [Изменение режима совместимости базы данных и использование хранилища запросов](../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md).  
  
-   **Службы Integration Services.**  
  
     Миграция пакетов служб Integration Services в формат [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Дополнительные сведения см. в разделе [Upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
-   **Службы Reporting Services:** в случае обновления методом новой установки восстановите ключи шифрования служб Reporting Services. Дополнительные сведения см. в разделе [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../reporting-services/install-windows/back-up-and-restore-reporting-services-encryption-keys.md).  
  
-   **Master Data Services:** обновите схему базы данных MDS и создайте веб-приложение SQL Server 2016. Дополнительные сведения см. в статье [Обновление служб Master Data Services](../../database-engine/install-windows/upgrade-master-data-services.md).  
  
-   **Службы качества данных:** обновите схему базы данных DQS и проверьте обновление этой схемы. Дополнительные сведения см. в статье [Обновление служб Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md).  
  
-   **Полнотекстовый поиск:** для обеспечения семантической согласованности результатов запросов заполните полнотекстовые каталоги повторно. Дополнительные сведения см. в разделе [Заполнение полнотекстовых индексов](../../relational-databases/search/populate-full-text-indexes.md).  
  
## Эта статья помогла вам? Мы слушаем  
 Какие сведения вы искали и удалось ли вам их найти? Мы прислушиваемся к вашим отзывам для совершенствования материалов. Отправляйте свои комментарии по адресу [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Complete%20the%20Database%20Engine%20Upgrade%20page).  
  
  