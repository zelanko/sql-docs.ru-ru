---
title: "Ведение журнала для пакетов с балансировкой нагрузки на удаленных серверах | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "журналы [службы Integration Services], удаленные пакеты"
ms.assetid: fd571567-b625-4f9a-8b7e-42c5c588b11b
caps.latest.revision: 24
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 24
---
# Ведение журнала для пакетов с балансировкой нагрузки на удаленных серверах
  Для администратора проще управлять журналами для всех дочерних пакетов, выполняющихся на разных серверах, когда все дочерние пакеты используют один регистратор и все они выполняют запись в одно назначение. Одним из способов создания общего файла журнала для всех дочерних пакетов является настройка дочерних пакетов на запись своих событий в регистратор служб SQL Server. Для всех пакетов можно задать использование одной базы данных, одного сервера и одного экземпляра сервера.  
  
 При просмотре журналов администратору достаточно подключиться к одному серверу, чтобы просмотреть файлы журналов для всех дочерних пакетов.  
  
## Связанные задачи  
 Дополнительные сведения о способах включения ведения журналов в пакете см. в разделе [Включение средств ведения журналов в SQL Server Data Tools](../../integration-services/performance/enable-package-logging-in-sql-server-data-tools.md).  
  
## См. также  
 [Ведение журналов в службах Integration Services (SSIS)](../../integration-services/performance/integration-services-ssis-logging.md)  
  
  