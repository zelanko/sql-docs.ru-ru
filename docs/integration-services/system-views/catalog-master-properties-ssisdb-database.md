---
title: "Catalog.master_properties (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00bfa716-5390-48e3-b30c-d954d5e0be47
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: 0fcbdca57c7764eaec758d2ad9ef3ab8675a3a9b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/08/2017

---
# <a name="catalogmasterproperties-ssisdb-database"></a>Catalog.master_properties (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Отображает свойства [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] шкалы Out Master.

|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Имя в масштабное развертывание master свойство.|  
|property_value|**nvarchar(max)**|Значение масштабирования master свойство.|

## <a name="remarks"></a>Замечания
В этом представлении отображается строка для каждого масштабирования master свойство. Это представление выводит, в частности, следующие свойства.

|Имя свойства|Description|  
|-------------------|-----------------| 
|**CLUSTER_LOGDB_SERVER**|SQL Server, на базе данных журналов находит в.|
|**LAST_ONLINE_TIME**|Время последнего при шкалы Out Master находится в оперативном режиме.|
|**MACHINE_IP**|IP-адрес компьютера.|
|**MACHINE_NAME**|Имя компьютера.|
|**MASTER_ADDRESS**|Конечная точка шкалы Out Master.|
|**MASTER_SERVICE_PORT**|Порт в конечной точке компонента шкалы Out Master.|
|**SSLCERT_THUMBPRINT**|Отпечаток сертификата шкалы Out Master.|

## <a name="permissions"></a>Permissions
Все члены роли базы данных public разрешениями на чтение для этого представления. 

