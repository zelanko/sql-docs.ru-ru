---
title: "Catalog.Executables доступны | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: bae22d0c-e190-426f-a074-c1d1170e8dd8
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: aa0d2d5df7c3c39b1ad33794ae11c1a34ffe72d4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogexecutables"></a>catalog.executables
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В этом представлении отображается по одной строке для каждого исполняемого объекта в указанном выполнении.  
  
 Исполняемый объект ― это задача или контейнер, добавленный в поток управления пакетом.  
  
|Имя столбца|**Тип данных**|Description|  
|-----------------|-------------------|-----------------|  
|executable_id|**bigint**|Уникальный идентификатор исполняемого объекта.|  
|execution_id|**bigint**|Уникальный идентификатор для экземпляра выполнения.|  
|executable_name|**nvarchar(4000)**|Имя исполняемого объекта.|  
|executable_guid|**nvarchar(38)**|Идентификатор GUID исполняемого объекта.|  
|package_name|**nvarchar(260)**|Имя пакета.|  
|путь к пакету|**nvarchar(max)**|Путь к пакету.|  
  
## <a name="permissions"></a>Permissions  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на экземпляр выполнения  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
## <a name="remarks"></a>Замечания  
  
