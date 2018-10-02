---
title: catalog.get_parameter_values (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 5b1aeaf7-c938-4aef-bafc-e4d7a82eb578
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f0307086f5dc8faa33801843cc20c2c375dc75c9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765972"
---
# <a name="cataloggetparametervalues-ssisdb-database"></a>catalog.get_parameter_values (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Обеспечивает разрешение и выборку значений параметров по умолчанию из проекта и соответствующих пакетов в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.get_parameter_values [ @folder_name = ] folder_name  
     , [ @project_name = ] project_name  
     , [ @package_name = ] package_name  
  [  , [ @reference_id = ] reference_id  ]  
  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name = ] *folder_name*  
 Имя папки, которая содержит проект. Параметр *folder_name* имеет тип **nvarchar(128)**.  
  
 [ @project_name = ] *project_name*  
 Имя проекта, где находятся параметры. Параметр *project_name* имеет тип **nvarchar(128)**.  
  
 [ @package_name = ] *package_name*  
 Имя пакета. Укажите имя пакета для извлечения всех параметров проекта и параметры из конкретного пакета. Укажите NULL для извлечения всех параметров проекта и параметров из всех пакетов. Параметр *package_name* имеет тип **nvarchar(260)**.  
  
 [ @reference_id = ] *reference_id*  
 Уникальный идентификатор ссылки на среду. Этот параметр является необязательным. Параметр *reference_id* имеет тип **bigint**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает таблицу следующего формата:  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|object_type|**smallint**|Тип параметра. Это значение равно `20` для параметра проекта и равно `30` для параметра пакета.|  
|parameter_data_type|**nvarchar(128)**|Тип данных параметра.|  
|parameter_name|**sysname**|Имя параметра.|  
|parameter_value|**sql_variant**|Значение параметра.|  
|sensitive|**bit**|Если значение равно `1`, значение параметра конфиденциально. Если значение равно `0`, то значение параметра не конфиденциально.|  
|required|**bit**|Если значение равно `1`, то значение параметра необходимо для начала выполнения. Если значение равно `0`, то значение параметра не является необходимым для начала выполнения.|  
|value_set|**bit**|Если значение равно `1`, то значение параметра было назначено. Если значение равно `0`, то значение параметра не было назначено.|  
  
> [!NOTE]  
>  Литеральные значения отображаются обычным текстом. Вместо конфиденциальных значений отображается **NULL**.  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ на проект и, если применимо, на указанную среду.  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Пакет не найден в указанной папке или проекте  
  
-   Пользователь не имеет соответствующих разрешений  
  
-   Указанный идентификатор среды не существует.  
  
  
