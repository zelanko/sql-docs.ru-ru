---
title: "Catalog.catalog_properties (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: e604a382-95c8-4764-b268-742eb5c6d4cf
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ca3d5da05126d5b71bf6d714f9e8449f9f5c8335
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcatalogproperties-ssisdb-database"></a>catalog.catalog_properties (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает свойства каталога служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Имя свойства каталога.|  
|property_value|**nvarchar(256)**|Значение свойства каталога.|  
  
## <a name="remarks"></a>Замечания  
 В этом представлении отображается строка для каждого свойства каталога. Это представление выводит, в частности, следующие свойства.  
  
|Имя свойства|Description|  
|-------------------|-----------------|  
|**ENCRYPTION_ALGORITHM**|Тип алгоритма шифрования конфиденциальных данных. Поддерживаемые значения: `DES`, `TRIPLE_DES`, `TRIPLE_DES_3KEY`, `DESX`, `AES_128`, `AES_192`, и `AES_256`. Примечание: База данных каталога должна быть в однопользовательском режиме для изменения этого свойства.|  
|**MAX_PROJECT_VERSIONS**|Количество новых версий проекта, хранимых в одном проекте. При включении очистки версий старые версии сверх этого количества будут удалены.|  
|**OPERATION_CLEANUP_ENABLED**|Если значение равно `TRUE`, подробности и сообщения операции старше **RETENTION_WINDOW** (в днях), удаляются из каталога. Если значение равно `FALSE`, все подробности и сообщения операции сохраняются в каталоге. Примечание. Задание [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет очистку операций.|  
|**RETENTION_WINDOW**|Срок (в днях) сохранения подробностей и сообщений операции в каталоге. Значение, равное `-1`, соответствует неограниченному сроку хранения. Примечание: Если очистка не требуется задать **OPERATION_CLEANUP_ENABLED** для **FALSE**.|  
|**VALIDATION_TIMEOUT**|Срок (в секундах), по истечении которого прекращаются невыполненные проверки.|  
|**VERSION_CLEANUP_ENABLED**|Если значение равно `TRUE`только **MAX_PROJECT_VERSIONS** количество версий проекта хранятся в каталоге и все остальные версии проекта удаляются. Если значение равно **FALSE**, все версии проекта хранятся в каталоге. Примечание. Задание [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет очистку операций.|  
|**SERVER_LOGGING_LEVEL**|Уровень ведения журнала по умолчанию для сервера служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|  
  
## <a name="permissions"></a>Permissions  
 Это представление требует применения одного из следующих разрешений:  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
  

