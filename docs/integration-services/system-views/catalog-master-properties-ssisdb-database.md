---
description: catalog.master_properties (база данных SSISDB)
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
ms.openlocfilehash: 09e13f54b3e7ee92ed72b055246ea1235845448f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422058"
---
# <a name="catalogmaster_properties-ssisdb-database"></a>catalog.master_properties (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

Отображает свойства мастера [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out.

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Имя свойства мастера Scale Out.|  
|property_value|**nvarchar(max)**|Значение свойства мастера Scale Out.|

## <a name="remarks"></a>Комментарии
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
