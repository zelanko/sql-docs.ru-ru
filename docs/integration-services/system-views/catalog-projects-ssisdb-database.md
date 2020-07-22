---
title: catalog.projects (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: a6b595e1-5227-47ce-8ee2-a28c1e1d5645
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a0975d296454c7528860ca65ae3cecfb47e276f
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912446"
---
# <a name="catalogprojects-ssisdb-database"></a>catalog.projects (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отображает подробные сведения для всех проектов, которые находятся в каталоге служб **SSISDB**.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|project_id|**bigint**|Уникальный идентификатор (ID) проекта.|  
|folder_id|**bigint**|Уникальный идентификатор папки, в которой хранится проект.|  
|name|**sysname**|Имя проекта.|  
|description|**nvarchar(1024)**|Необязательное описание проекта.|  
|project_format_version|**int**|Версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая использовалась для разработки проекта.|  
|deployed_by_sid|**varbinary(85)**|Идентификатор безопасности (SID) пользователя, установившего проект.|  
|deployed_by_name|**nvarchar(128)**|Имя пользователя, установившего проект.|  
|last_deployed_time|**datetimeoffset(7)**|Дата и время развертывания или повторного развертывания проекта.|  
|created_time|**datetimeoffset(7)**|Дата и время создания проекта.|  
|object_version_lsn|**bigint**|Версия проекта. Не гарантируется, что это число будет последовательным.|  
|validation_status|**char(1)**|Состояние проверки.|  
|last_validation_time|**datetimeoffset(7)**|Время последней проверки.|  
  
## <a name="remarks"></a>Remarks  
 В этом представлении отображается строка для каждого проекта в каталоге.  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на проект  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**.  
  
> [!NOTE]  
>  Наличие разрешения READ на проект влечет за собой также наличие разрешения READ на все пакеты и ссылки на среду, связанные с этим проектом. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
