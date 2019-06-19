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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 34c282905f5314772a11318bf7c3eb60650e96fe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65714961"
---
# <a name="catalogexecutablestatistics"></a>catalog.executable_statistics 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Показывает строку для каждого запускаемого исполняемого объекта, включая все повторы.  
  
 Исполняемый объект ― это задача или контейнер, добавленный в поток управления пакетом.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|Statistics_id|BIGINT|Уникальный идентификатор данных.|  
|Execution_id|BIGINT|Уникальный идентификатор для экземпляра выполнения.<br /><br /> Представление catalog.executions предоставляет дополнительные сведения о выполнении. Дополнительные сведения см. в разделе [catalog.executions (база данных SSISDB)](../../integration-services/system-views/catalog-executions-ssisdb-database.md).|  
|Executable_id|BIGINT|Уникальный идентификатор компонента пакета.<br /><br /> В представлении catalog.executables доступны дополнительные сведения об исполняемых объектах. Дополнительные сведения см. в разделе [catalog.executables](../../integration-services/system-views/catalog-executables.md).|  
|Execution_path|nvarchar(max)|Полный путь выполнения для компонента пакета, включая все повторы компонента.|  
|Start_time|datetimeoffset(7)|Время, когда исполняемый объект переходит в фазу предысполнения.|  
|End_time|datetimeoffset(7)|Время, когда исполняемый объект переходит в фазу после исполнения.|  
|Execution_duration|ssNoversion|Продолжительность выполнения исполняемого объекта. Значение указывается в миллисекундах.|  
|Execution_result|smallint|Допустимы следующие значения:<br /><br /> 0 = успешное завершение<br /><br /> 1 = неуспешное завершение.<br /><br /> 2 = завершение<br /><br /> 3 = отмена.|  
|Execution_value|sql_variant|Значение, возвращаемое при выполнении. Это значение определяется пользователем.|  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует одного из следующих разрешений:  
  
-   разрешение READ на экземпляр выполнения.  
  
-   Членство в роли базы данных **ssis_admin**.  
  
-   Членство в роли сервера **sysadmin**.  
  
  
