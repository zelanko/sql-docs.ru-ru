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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 04f04b8847dbdfac12f5b78c3eabb3b493e2d895
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58275226"
---
# <a name="catalogmasterproperties-ssisdb-database"></a>catalog.master_properties (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Отображает свойства мастера [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out.

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Имя свойства мастера Scale Out.|  
|property_value|**nvarchar(max)**|Значение свойства мастера Scale Out.|

## <a name="remarks"></a>Remarks
В этом представлении отображается строка для каждого свойства мастера Scale Out. Это представление выводит, в частности, следующие свойства.

|Имя свойства|Описание|  
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
