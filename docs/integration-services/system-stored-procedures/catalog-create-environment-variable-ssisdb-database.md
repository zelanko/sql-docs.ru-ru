---
title: "Catalog.create_environment_variable (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 91ed017b-6567-4bf2-b9f1-e2b5c70a5343
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 5636651cccbb43c6c1627d1f28eccd9b3f9b5b0d
ms.contentlocale: ru-ru
ms.lasthandoff: 10/20/2017

---
# <a name="catalogcreateenvironmentvariable-ssisdb-database"></a>catalog.create_environment_variable (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Создайте переменную среды в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.create_environment_variable [@folder_name =] folder_name  
    , [@environment_name =] environment_name  
    , [@variable_name =] variable_name  
    , [@data_type =] data_type  
    , [@sensitive =] sensitive  
    , [@value =] value  
    , [@description =] description  
```  
  
## <a name="arguments"></a>Аргументы  
 [@folder_name =] *имя_папки*  
 Имя папки, которая содержит среду. *Имя_папки* — **nvarchar(128)**.  
  
 [@environment_name =] *environment_name*  
 Имя среды. *Environment_name* — **nvarchar(128)**.  
  
 [@variable_name =] *имя_переменной*  
 Имя переменной среды. *Имя_переменной* — **nvarchar(128)**.  
  
 [@data_type =] *data_type*  
 Тип данных переменной. Поддерживаемые типы данных переменной среды **логическое**, **байтов**, **DateTime**, **двойные**, **Int16**, **Int32**, **Int64**, **один**, **строка**, **UInt32**и  **UInt64**. Типы данных переменной среды не поддерживаются: **Char**, **DBNull**, **объекта**, и **Sbyte**. Тип данных *data_type* параметр **nvarchar(128)**.  
  
 [@sensitive =] *конфиденциальных*  
 Указывает, содержит переменная конфиденциальное значение или нет. Значение `1` указывает, что значение переменной среды является конфиденциальным, а значение `0` — что оно таковым не является. Конфиденциальное значение шифруется при его сохранении. Значение, которое не является конфиденциальным хранится в виде обычного текста. *Конфиденциальных* — **бит**.  
  
 [@value =] *значение*  
 Значение переменной среды. *Значение* — **sql_variant**.  
  
 [@description =] *описание*  
 Описание переменной среды. *Значение* — **nvarchar(1024)**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY для среды  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Недопустимое имя папки, имя среды или имя переменной среды  
  
-   Имя переменной уже существует в среде  
  
-   Пользователь не имеет соответствующих разрешений  
  
## <a name="remarks"></a>Замечания  
 Переменная среды — это удобный способ присвоения значения параметру проекта или параметру пакета для использования во время выполнения пакета. Переменные среды позволяют организовать значения параметров. Имена переменных должны быть уникальными в пределах среды.  
  
 Хранимая процедура проверяет тип данных переменной, чтобы убедиться в том, что каталог служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] его поддерживает.  
  
> [!TIP]  
>  Рассмотрите возможность использования **Int16** в тип данных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] вместо неподдерживаемого **Sbyte** тип данных.  
  
 Значение, передаваемое в эту хранимую процедуру *значение* параметр преобразуется из [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] тип данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных согласно следующей таблице:  
  
|Тип данных служб Integration Services|Тип данных SQL Server|  
|------------------------------------|--------------------------|  
|**Логическое значение**|**bit**|  
|**Байт**|**двоичный**, **varbinary**|  
|**DateTime**|**DateTime**, **datetime2**, **datetimeoffset**, **smalldatetime**|  
|**Double**|Точное числовое значение: **десятичное**, **числовое**; Приблизительное числовое: **float**, **real**|  
|**Int16**|**smallint**|  
|**Int32**|**int**|  
|**Int64**|**bigint**|  
|**Один**|Точное числовое значение: **десятичное**, **числовое**; Приблизительное числовое: **float**, **real**|  
|**Строковые значения**|**varchar**, **nvarchar**, **char**|  
|**UInt32**|**int** (**int** является близкое доступное сопоставление с **Uint32**.)|  
|**UInt64**|**bigint** (**int** является близкое доступное сопоставление с **Uint64**.)|  
  
  

