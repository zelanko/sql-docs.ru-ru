---
title: catalog.master_properties (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 00bfa716-5390-48e3-b30c-d954d5e0be47
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3ce06430094825bf3268836657661930fea058e4
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71296625"
---
# <a name="catalogmaster_properties-ssisdb-database"></a>catalog.master_properties (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Отображает свойства мастера [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out.

|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Имя свойства мастера горизонтального увеличения масштаба.|  
|property_value|**nvarchar(max)**|Значение свойства мастера горизонтального увеличения масштаба.|

## <a name="remarks"></a>Remarks
В этом представлении отображается строка для каждого свойства мастера горизонтального увеличения масштаба. Это представление выводит, в частности, следующие свойства.

|Имя свойства|Description|  
|-------------------|-----------------| 
|**CLUSTER_LOGDB_SERVER**|SQL Server, где находится база данных журналов.|
|**LAST_ONLINE_TIME**|Время последнего подключения мастера горизонтального увеличения масштаба к сети.|
|**MACHINE_IP**|IP-адрес компьютера.|
|**MACHINE_NAME**|Имя компьютера.|
|**MASTER_ADDRESS**|Конечная точка мастера горизонтального увеличения масштаба.|
|**MASTER_SERVICE_PORT**|Порт в конечной точке мастера горизонтального увеличения масштаба.|
|**SSLCERT_THUMBPRINT**|Отпечаток сертификата мастера горизонтального увеличения масштаба.|

## <a name="permissions"></a>Разрешения
Все члены роли общей базы данных имеют разрешения на чтение для этого представления. 
