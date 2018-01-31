---
title: "catalog.restore_project (база данных SSISDB) | Документы Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 8adee525-579b-4d2f-b807-e2ecc07fb2e9
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6933aa64b1a2c660e7328238ad52442d500bd496
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="catalogrestoreproject-ssisdb-database"></a>catalog.restore_project (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Восстанавливает проект в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с переходом к предыдущей версии.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.restore_project [ @folder_name = ] folder_name  
    , [ @project_name = ] project _name  
    , [ @object_version_lsn = ] object_version_lsn  
  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name = ] *folder_name*  
 Имя папки, которая содержит проект. Параметр *folder_name* имеет тип **nvarchar(128)**.  
  
 [ @project _name = ] *project_name*  
 Имя проекта. Параметр *project_name* имеет тип **nvarchar(128)**.  
  
 [ @object_version_lsn = ] *object_version_lsn*  
 Версия проекта. Параметр *object_version_lsn* имеет тип **bigint**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Детали проекта возвращаются в формате **varbinary(MAX)** как часть результирующего набора, если обнаружено имя проекта *project_name*.  
  
 Если возвращается сообщение **NO RESULT SET**, проект не может быть восстановлен в указанной папке.  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на проект  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Версия проекта не существует или не соответствует имени проекта  
  
-   Проект не существует  
  
-   Пользователь не имеет соответствующих разрешений  
  
## <a name="remarks"></a>Remarks  
 Когда восстанавливается проект, всем параметрам присваиваются значения по умолчанию, а все ссылки на среды остаются без изменения. Максимальное количество версий проекта, хранимых в каталоге, задается свойством каталога **MAX_VERSIONS_PER_PROJECT**, как показано в представлении [catalog_property](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md).  
  
> [!WARNING]  
>  После восстановления проекта ссылки на среду могут стать недействительными.  
  
  
