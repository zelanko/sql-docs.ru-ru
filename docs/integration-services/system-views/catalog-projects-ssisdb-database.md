---
title: "Catalog.Projects (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a6b595e1-5227-47ce-8ee2-a28c1e1d5645
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 668890ae464deb8dfa029eab38b608fee12af0ca
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogprojects-ssisdb-database"></a>catalog.projects (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает подробные сведения для всех проектов, которые отображаются в **SSISDB** каталога.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|project_id|**bigint**|Уникальный идентификатор (ID) проекта.|  
|folder_id|**bigint**|Уникальный идентификатор папки, в которой хранится проект.|  
|имя|**sysname**|Имя проекта.|  
|description|**nvarchar(1024)**|Необязательное описание проекта.|  
|project_format_version|**int**|Версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая использовалась для разработки проекта.|  
|deployed_by_sid|**varbinary(85)**|Идентификатор безопасности (SID) пользователя, установившего проект.|  
|deployed_by_name|**nvarchar(128)**|Имя пользователя, установившего проект.|  
|last_deployed_time|**DateTimeOffset(7)**|Дата и время развертывания или повторного развертывания проекта.|  
|created_time|**DateTimeOffset(7)**|Дата и время создания проекта.|  
|object_version_lsn|**bigint**|Версия проекта. Не гарантируется, что это число будет последовательным.|  
|validation_status|**char(1)**|Состояние проверки.|  
|last_validation_time|**DateTimeOffset(7)**|Время последней проверки.|  
  
## <a name="remarks"></a>Замечания  
 В этом представлении отображается строка для каждого проекта в каталоге.  
  
## <a name="permissions"></a>Permissions  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на проект  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера.  
  
> [!NOTE]  
>  Наличие разрешения READ на проект влечет за собой также наличие разрешения READ на все пакеты и ссылки на среду, связанные с этим проектом. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  

