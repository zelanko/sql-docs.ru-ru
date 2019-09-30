---
title: catalog.set_environment_property (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: a345675b-d32e-4624-96cf-ec656730b114
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d8c455243f6ca903f61bfa7ad6ef6d88e544a258
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71295421"
---
# <a name="catalogset_environment_property-ssisdb-database"></a>catalog.set_environment_property (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Задает свойство среды в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.set_environment_property [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @property_name = ] property_name  
    , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name = ] *folder_name*  
 Имя папки, которая содержит среду. Параметр *folder_name* имеет тип **nvarchar(128)** .  
  
 [ @environment_name = ] *environment_name*  
 Имя среды. Параметр *environment_name* имеет тип **nvarchar(128)** .  
  
 [ @property_name = ] *property_name*  
 Имя свойства среды. Параметр *property_name* имеет тип **nvarchar(128)** .  
  
 [ @property_value = ] *property_value*  
 Значение свойства среды. Параметр *property_value* имеет тип **nvarchar(1024)** .  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY для среды  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Недопустимое имя папки  
  
-   Недопустимое имя свойства  
  
-   Недопустимое имя среды  
  
## <a name="remarks"></a>Remarks  
 В этом выпуске может быть задано только свойство `Description`. Значение свойства `Description` не может иметь длину более 4000 символов.  
  
  
