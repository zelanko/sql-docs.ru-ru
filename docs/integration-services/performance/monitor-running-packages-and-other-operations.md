---
title: "Наблюдение за выполнением пакетов и других операций | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cbbcd79f-ab9b-46ec-84cb-4821c1d16b99
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# Наблюдение за выполнением пакетов и других операций
  Вы можете отслеживать выполнения пакета [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , проверки проекта и другие операции с помощью одного или нескольких из следующих средств. Такие средства, как отводы данных, доступны только для проектов, которые развертываются на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
-   Журналы  
  
     Дополнительные сведения см. в разделе [Ведение журналов в службах Integration Services (SSIS)](../../integration-services/performance/integration-services-ssis-logging.md).  
  
-   Отчеты  
  
     Дополнительные сведения см. в статье [Reports for the Integration Services Server](../../integration-services/performance/reports-for-the-integration-services-server.md).  
  
-   Представления  
  
     Дополнительные сведения см. в статье [Представления (каталог служб Integration Services)](../../integration-services/system-views/views-integration-services-catalog.md).  
  
-   Счетчики производительности  
  
     Дополнительные сведения см. в статье [Performance Counters](../../integration-services/performance/performance-counters.md).  
  
-   Отводы данных  
  
## Типы операций  
 В каталоге **SSISDB** на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] отслеживаются операции нескольких разных типов. Каждая операция может иметь несколько связанных с ней сообщений. Каждое сообщение можно отнести к одному из нескольких разных типов. Например, сообщение может иметь тип «информация», «предупреждение» или «ошибка». Полный список типов сообщений см. в документации по представлению Transact-SQL [catalog.operation_messages (база данных SSISDB)](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md). Полный список типов операций см. в статье [catalog.operations (база данных SSISDB)](../../integration-services/system-views/catalog-operations-ssisdb-database.md).  
  
 Для указания состояния операции используются девять различных типов состояний. Полный список типов состояний см. в представлении [catalog.operations (база данных SSISDB)](../../integration-services/system-views/catalog-operations-ssisdb-database.md)  
  
## См. также  
 Запись в блоге [Общие сведения о T-SQL API служб SSIS](http://go.microsoft.com/fwlink/?LinkId=249051) на сайте blogs.msdn.com.  
  
  