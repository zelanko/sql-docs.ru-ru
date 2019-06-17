---
title: Наблюдение за выполнением пакетов и других операций | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cbbcd79f-ab9b-46ec-84cb-4821c1d16b99
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6f6a4e147c90fe7c4f25f5c8b821b4787ec3be71
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62766986"
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
  
  
