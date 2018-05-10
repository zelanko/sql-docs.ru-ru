---
title: catalog.master_properties (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 00bfa716-5390-48e3-b30c-d954d5e0be47
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c48f9e25d0a662f5f1f756b16b7f3edbe361de29
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="catalogmasterproperties-ssisdb-database"></a>catalog.master_properties (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Отображает свойства мастера [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out.

|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Имя свойства мастера Scale Out.|  
|property_value|**nvarchar(max)**|Значение свойства мастера Scale Out.|

## <a name="remarks"></a>Remarks
В этом представлении отображается строка для каждого свойства мастера Scale Out. Это представление выводит, в частности, следующие свойства.

|Имя свойства|Description|  
|-------------------|-----------------| 
|**CLUSTER_LOGDB_SERVER**|SQL Server, где находится база данных журналов.|
|**LAST_ONLINE_TIME**|Время последнего подключения мастера Scale Out к сети.|
|**MACHINE_IP**|IP-адрес компьютера.|
|**MACHINE_NAME**|Имя компьютера.|
|**MASTER_ADDRESS**|Конечная точка мастера Scale Out.|
|**MASTER_SERVICE_PORT**|Порт в конечной точке мастера Scale Out.|
|**SSLCERT_THUMBPRINT**|Отпечаток сертификата мастера Scale Out.|

## <a name="permissions"></a>Разрешения
Все члены роли общей базы данных имеют разрешения на чтение для этого представления. 
