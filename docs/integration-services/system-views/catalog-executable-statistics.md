---
title: "Catalog.executable_statistics | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 3dda28d6-10d8-4294-9b5e-a6048c07faf9
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: bc671da319ee9e8ce71d98df001c3989d497a096
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogexecutablestatistics"></a>catalog.executable_statistics
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Показывает строку для каждого запускаемого исполняемого объекта, включая все повторы.  
  
 Исполняемый объект ― это задача или контейнер, добавленный в поток управления пакетом.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|Statistics_id|bigint|Уникальный идентификатор данных.|  
|Execution_id|bigint|Уникальный идентификатор для экземпляра выполнения.<br /><br /> Представление catalog.executions предоставляет дополнительные сведения о выполнении. Дополнительные сведения см. в разделе [catalog.executions &#40; База данных SSISDB &#41; ](../../integration-services/system-views/catalog-executions-ssisdb-database.md).|  
|Executable_id|bigint|Уникальный идентификатор компонента пакета.<br /><br /> В представлении catalog.executables доступны дополнительные сведения об исполняемых объектах. Дополнительные сведения см. в разделе [Catalog.Executables доступны](../../integration-services/system-views/catalog-executables.md).|  
|Execution_path|nvarchar(max)|Полный путь выполнения для компонента пакета, включая все повторы компонента.|  
|Start_time|datetimeoffset(7)|Время, когда исполняемый объект переходит в фазу предысполнения.|  
|End_time|datetimeoffset(7)|Время, когда исполняемый объект переходит в фазу после исполнения.|  
|Execution_duration|int|Продолжительность выполнения исполняемого объекта. Значение указывается в миллисекундах.|  
|Execution_result|smallint|Допустимы следующие значения:<br /><br /> 0 = успешное завершение<br /><br /> 1 = неуспешное завершение.<br /><br /> 2 = завершение<br /><br /> 3 = отмена.|  
|Execution_value|sql_variant|Значение, возвращаемое при выполнении. Это значение определяется пользователем.|  
  
## <a name="permissions"></a>Permissions  
 Это представление требует одного из следующих разрешений:  
  
-   разрешение READ на экземпляр выполнения.  
  
-   Членство в **ssis_admin** роли базы данных.  
  
-   Членство в **sysadmin** роли сервера.  
  
  

