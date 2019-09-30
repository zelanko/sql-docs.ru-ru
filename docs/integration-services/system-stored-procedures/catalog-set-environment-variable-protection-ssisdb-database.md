---
title: catalog.set_environment_variable_protection (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 005b6b2f-a5d9-4ea4-8d4e-beed6ab33c0d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fc67461545e7a1585e5f45eb35c52a5630248391
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71295322"
---
# <a name="catalogset_environment_variable_protection-ssisdb-database"></a>catalog.set_environment_variable_protection (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Задает бит конфиденциальности переменной среды в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.set_environment_variable_protection [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @variable_name = ] variable_name  
    , [ @sensitive = ] sensitive  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name = ] *folder_name*  
 Имя папки, которая содержит среду. Параметр *folder_name* имеет тип **nvarchar(128)** .  
  
 [ @environment_name = ] *environment_name*  
 Имя среды. Параметр *environment_name* имеет тип **nvarchar(128)** .  
  
 [ @variable_name = ] *variable_name*  
 Имя переменной среды. Параметр *variable_name* имеет тип **nvarchar(128)** .  
  
 [ @sensitive = ] *sensitive*  
 Указывает, содержит переменная конфиденциальное значение или нет. Значение `1` указывает, что значение переменной среды является конфиденциальным, а значение `0` — что оно таковым не является. Конфиденциальное значение шифруется при его сохранении. Значение, которое не является конфиденциальным, сохраняется в формате открытого текста. Параметр *sensitive* имеет тип **bit**.  
  
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
  
-   Недопустимое имя среды  
  
-   Недопустимое имя переменной среды  
  
-   Пользователь не имеет соответствующих разрешений  
  
  
