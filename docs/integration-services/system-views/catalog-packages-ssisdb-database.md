---
title: catalog.packages (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
helpviewer_keywords:
- packages view [Integration Services]
- catalog.packages view [Integration Services]
ms.assetid: a634e94d-f492-4dfd-9611-a35f545106a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aea0d3c07482c7c54dc5adb8956b290791f29111
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71295170"
---
# <a name="catalogpackages-ssisdb-database"></a>catalog.packages (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает подробные сведения для всех пакетов, которые появляются в каталоге служб **SSISDB**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|package_id|**bigint**|Уникальный идентификатор (ID) пакета.|  
|name|**nvarchar(256)**|Уникальное имя пакета.|  
|package_guid|**uniqueidentifier**|Глобально уникальный идентификатор (GUID), определяющий пакет.|  
|description|**nvarchar(1024)**|Необязательное описание пакета.|  
|package_format_version|**int**|Версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая использовалась для разработки пакета.|  
|version_major|**int**|Полнофункциональная версия пакета.|  
|version_minor|**int**|Сокращенная версия пакета.|  
|version_build|**int**|Версия сборки пакета.|  
|version_comments|**nvarchar(1024)**|Необязательные примечания к версии пакета.|  
|version_guid|**uniqueidentifier**|Идентификатор GUID, который уникально идентифицирует версию пакета.|  
|project_id|**bigint**|Уникальный идентификатор проекта.|  
|entry_point|**bit**|Значение `1` указывает, что пакет должен быть запущен непосредственно. Значение `0` указывает, что пакет должен быть запущен при помощи другого пакета с задачей «Выполнение пакета». Значение по умолчанию — `1`.|  
|validation_status|**char(1)**|Состояние проверки.|  
|last_validation_time|**datetimeoffset(7)**|Время последней проверки.|  
  
## <a name="remarks"></a>Remarks  
 В этом представлении отображается строка для каждого пакета в каталоге.  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на соответствующий проект  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**.  
  
> [!NOTE]  
>  Наличие разрешения READ на проект влечет за собой также наличие разрешения READ на все пакеты и ссылки на среду, связанные с этим проектом. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
