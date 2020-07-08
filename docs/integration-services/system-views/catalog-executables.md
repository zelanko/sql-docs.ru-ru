---
title: catalog.executables | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: bae22d0c-e190-426f-a074-c1d1170e8dd8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 080bd33f6864355dbd0f6eb58903b1796670ed26
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85673017"
---
# <a name="catalogexecutables"></a>catalog.executables 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  В этом представлении отображается по одной строке для каждого исполняемого объекта в указанном выполнении.  
  
 Исполняемый объект ― это задача или контейнер, добавленный в поток управления пакетом.  
  
|Имя столбца|**Data type**|Description|  
|-----------------|-------------------|-----------------|  
|executable_id|**bigint**|Уникальный идентификатор исполняемого объекта.|  
|execution_id|**bigint**|Уникальный идентификатор для экземпляра выполнения.|  
|executable_name|**nvarchar(4000)**|Имя исполняемого объекта.|  
|executable_guid|**nvarchar(38)**|Идентификатор GUID исполняемого объекта.|  
|package_name|**nvarchar(260)**|Имя пакета.|  
|путь к пакету|**nvarchar(max)**|Путь к пакету.|  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на экземпляр выполнения  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
## <a name="remarks"></a>Remarks  
  
