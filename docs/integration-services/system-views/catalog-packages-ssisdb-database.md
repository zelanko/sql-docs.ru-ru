---
title: "Catalog.Packages (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- packages view [Integration Services]
- catalog.packages view [Integration Services]
ms.assetid: a634e94d-f492-4dfd-9611-a35f545106a1
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f836c2b1bdf59f157f10abb708ed55f99dfc9f0f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogpackages-ssisdb-database"></a>catalog.packages (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает подробные сведения для всех пакетов, которые отображаются в **SSISDB** каталога.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|package_id|**bigint**|Уникальный идентификатор (ID) пакета.|  
|имя|**nvarchar(256)**|Уникальное имя пакета.|  
|package_guid|**uniqueidentifier**|Глобально уникальный идентификатор (GUID), определяющий пакет.|  
|description|**nvarchar(1024)**|Необязательное описание пакета.|  
|package_format_version|**int**|Версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая использовалась для разработки пакета.|  
|version_major|**int**|Полнофункциональная версия пакета.|  
|version_minor|**int**|Сокращенная версия пакета.|  
|version_build|**int**|Версия сборки пакета.|  
|version_comments|**nvarchar(1024)**|Необязательные примечания к версии пакета.|  
|version_guid|**uniqueidentifier**|Идентификатор GUID, который уникально идентифицирует версию пакета.|  
|project_id|**bigint**|Уникальный идентификатор проекта.|  
|точка входа|**bit**|Значение `1` указывает, что пакет должен быть запущен непосредственно. Значение `0` указывает, что пакет должен быть запущен при помощи другого пакета с задачей «Выполнение пакета». Значение по умолчанию — `1`.|  
|validation_status|**char(1)**|Состояние проверки.|  
|last_validation_time|**DateTimeOffset(7)**|Время последней проверки.|  
  
## <a name="remarks"></a>Замечания  
 В этом представлении отображается строка для каждого пакета в каталоге.  
  
## <a name="permissions"></a>Permissions  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на соответствующий проект  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера.  
  
> [!NOTE]  
>  Наличие разрешения READ на проект влечет за собой также наличие разрешения READ на все пакеты и ссылки на среду, связанные с этим проектом. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
