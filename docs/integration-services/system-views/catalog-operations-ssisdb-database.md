---
title: "Catalog.Operations (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- operations view [Integration Services]
- catalog.operations view [Integration Services]
ms.assetid: 9455c5b1-60ff-45fc-8599-cc3abbd6daf5
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f9d1969e9fe7bcb2104003cfab057effcd35da5d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogoperations-ssisdb-database"></a>catalog.operations (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает подробные сведения обо всех операциях в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|operation_id|**bigint**|Уникальный идентификатор (ID) операции.|  
|operation_type|**smallint**|Тип операции.|  
|created_time|**datetimeoffset**|Время создания операции.|  
|object_type|**smallint**|Тип объекта, затронутого операцией. Объект может представлять собой папку (`10`), проект (`20`), пакет (`30`), среду (`40`) или экземпляр выполнения (`50`).|  
|object_id|**bigint**|Идентификатор объекта, затронутого операцией.|  
|object_name|**nvarchar(260)**|Имя объекта.|  
|status|**int**|Состояние операции. Возможными значениями являются: создана (`1`), запущена (`2`), отменена (`3`), завершена неуспешно (`4`), ожидает (`5`), завершена непредвиденно (`6`), выполнена успешно (`7`), остановлена (`8`) и завершена (`9`).|  
|start_time|**datetimeoffset**|Время начала операции.|  
|end_time|**datetimeoffsset**|Время окончания операции.|  
|caller_sid|**varbinary(85)**|Идентификатор безопасности (SID) пользователя, если для входа в систему использовалась проверка подлинности Windows.|  
|caller_name|**nvarchar(128)**|Имя учетной записи, в которой выполнена операция.|  
|process_id|**int**|Идентификатор внешнего процесса, если это применимо.|  
|stopped_by_sid|**varbinary(85)**|Идентификатор безопасности пользователя, который остановил операцию.|  
|stopped_by_name|**nvarchar(128)**|Имя пользователя, который остановил операцию.|  
|server_name|**nvarchar(128)**|Сведения об экземпляре и сервере Windows для указанного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|machine_name|**nvarchar(128)**|Имя компьютера, на котором запущен экземпляр сервера.|  
  
## <a name="remarks"></a>Замечания  
 В этом представлении отображается одна строка для каждой операции в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Это позволяет администратору перечислить все логические операции, выполняемые на сервере, например развертывание проекта или выполнение пакета.  
  
 В этом представлении отображаются следующие типы операций, как указано в **operation_type** столбца:  
  
|**operation_type** значение|**operation_type** описание|**object_id** описание|**object_name** описание|  
|-------------------------------|-------------------------------------|--------------------------------|----------------------------------|  
|`1`|Инициализация служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|**NULL**|**NULL**|  
|`2`|Окно сохранения<br /><br /> (Задание агента SQL Server)|**NULL**|**NULL**|  
|`3`|MaxProjectVersion<br /><br /> (Задание агента SQL Server)|**NULL**|**NULL**|  
|`101`|**deploy_project**<br /><br /> (Хранимая процедура)|Идентификатор проекта|Имя проекта|  
|`106`|**restore_project**<br /><br /> (Хранимая процедура)|Идентификатор проекта|Имя проекта|  
|`200`|**create_execution** и **start_execution**<br /><br /> (Хранимые процедуры)|Идентификатор проекта|**NULL**|  
|`202`|**stop_operation**<br /><br /> (Хранимая процедура)|Идентификатор проекта|**NULL**|  
|`300`|**validate_project**<br /><br /> (Хранимая процедура)|Идентификатор проекта|Имя проекта|  
|`301`|**validate_package**<br /><br /> (Хранимая процедура)|Идентификатор проекта|Имя пакета|  
|`1000`|**configure_catalog**<br /><br /> (Хранимая процедура)|**NULL**|**NULL**||  
  
## <a name="permissions"></a>Permissions  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ по отношению к операции  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  

