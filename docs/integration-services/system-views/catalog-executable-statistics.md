---
title: catalog.executable_statistics | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 3dda28d6-10d8-4294-9b5e-a6048c07faf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2e1e5d79841997a2adabc567e8b47b68f8c179e1
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912640"
---
# <a name="catalogexecutable_statistics"></a>catalog.executable_statistics 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Показывает строку для каждого запускаемого исполняемого объекта, включая все повторы.  
  
 Исполняемый объект ― это задача или контейнер, добавленный в поток управления пакетом.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|Statistics_id|BIGINT|Уникальный идентификатор данных.|  
|Execution_id|BIGINT|Уникальный идентификатор для экземпляра выполнения.<br /><br /> Представление catalog.executions предоставляет дополнительные сведения о выполнении. Дополнительные сведения см. в разделе [catalog.executions (база данных SSISDB)](../../integration-services/system-views/catalog-executions-ssisdb-database.md).|  
|Executable_id|BIGINT|Уникальный идентификатор компонента пакета.<br /><br /> В представлении catalog.executables доступны дополнительные сведения об исполняемых объектах. Дополнительные сведения см. в разделе [catalog.executables](../../integration-services/system-views/catalog-executables.md).|  
|Execution_path|nvarchar(max)|Полный путь выполнения для компонента пакета, включая все повторы компонента.|  
|Start_time|datetimeoffset(7)|Время, когда исполняемый объект переходит в фазу предысполнения.|  
|End_time|datetimeoffset(7)|Время, когда исполняемый объект переходит в фазу после исполнения.|  
|Execution_duration|INT|Продолжительность выполнения исполняемого объекта. Значение указывается в миллисекундах.|  
|Execution_result|smallint|Допустимы следующие значения:<br /><br /> 0 = успешное завершение<br /><br /> 1 = неуспешное завершение.<br /><br /> 2 = завершение<br /><br /> 3 = отмена.|  
|Execution_value|sql_variant|Значение, возвращаемое при выполнении. Это значение определяется пользователем.|  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует одного из следующих разрешений:  
  
-   разрешение READ на экземпляр выполнения.  
  
-   Членство в роли базы данных **ssis_admin**.  
  
-   Членство в роли сервера **sysadmin**.  
  
  
