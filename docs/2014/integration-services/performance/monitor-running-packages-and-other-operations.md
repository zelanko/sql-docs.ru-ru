---
title: Мониторинг выполнения пакетов и других операций | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cbbcd79f-ab9b-46ec-84cb-4821c1d16b99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 628b62d9c8e01d0dc0bf641551de67c3838a4504
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85423251"
---
# <a name="monitoring-for-package-executions-and-other-operations"></a>Наблюдение за выполнением пакетов и других операций
  Вы можете отслеживать выполнения пакета [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , проверки проекта и другие операции с помощью одного или нескольких из следующих средств. Такие средства, как отводы данных, доступны только для проектов, которые развертываются на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
-   Журналы  
  
     Дополнительные сведения см. в разделе [Ведение журналов в службах Integration Services (SSIS)](integration-services-ssis-logging.md).  
  
-   Отчеты  
  
     Дополнительные сведения см. в статье [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).  
  
-   Представления  
  
     Дополнительные сведения см. в статье [Представления (каталог служб Integration Services)](/sql/integration-services/system-views/views-integration-services-catalog).  
  
-   Счетчики производительности  
  
     Дополнительные сведения см. в статье [Performance Counters](performance-counters.md).  
  
-   Отводы данных  
  
## <a name="operation-types"></a>Типы операций  
 В каталоге `SSISDB` на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] отслеживаются операции нескольких разных типов. Каждая операция может иметь несколько связанных с ней сообщений. Каждое сообщение можно отнести к одному из нескольких разных типов. Например, сообщение может иметь тип «информация», «предупреждение» или «ошибка». Полный список типов сообщений см. в документации по представлению Transact-SQL [catalog.operation_messages (база данных SSISDB)](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database). Полный список типов операций см. в статье [catalog.operations (база данных SSISDB)](/sql/integration-services/system-views/catalog-operations-ssisdb-database).  
  
 Для указания состояния операции используются девять различных типов состояний. Полный список типов состояний см. в представлении [catalog.operations (база данных SSISDB)](/sql/integration-services/system-views/catalog-operations-ssisdb-database)  
  
## <a name="related-content"></a>См. также  
 Запись в блоге [Общие сведения о T-SQL API служб SSIS](https://go.microsoft.com/fwlink/?LinkId=249051)на сайте blogs.msdn.com.  
  
  
