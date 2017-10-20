---
title: "Catalog.set_environment_variable_protection (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 005b6b2f-a5d9-4ea4-8d4e-beed6ab33c0d
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6d282ca675a35e84f2d283d3ad85b15039a15e52
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetenvironmentvariableprotection-ssisdb-database"></a>catalog.set_environment_variable_protection (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Задает бит конфиденциальности переменной среды в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
set_environment_variable_protection [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @variable_name = ] variable_name  
    , [ @is_sensitive = ] is_sensitive  
  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name =] *имя_папки*  
 Имя папки, которая содержит среду. *Имя_папки* — **nvarchar(128)**.  
  
 [ @environment_name =] *environment_name*  
 Имя среды. *Environment_name* — **nvarchar(128)**.  
  
 [ @variable_name =] *имя_переменной*  
 Имя переменной среды. *Имя_переменной* — **nvarchar(128)**.  
  
 [ @sensitive =] *конфиденциальных*  
 Указывает, содержит переменная конфиденциальное значение или нет. Значение `1` указывает, что значение переменной среды является конфиденциальным, а значение `0` — что оно таковым не является. Конфиденциальное значение шифруется при его сохранении. Значение, которое не является конфиденциальным, сохраняется в формате открытого текста. *Конфиденциальных* параметр **бит**.  
  
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
  
-   Недопустимое имя папки  
  
-   Недопустимое имя среды  
  
-   Недопустимое имя переменной среды  
  
-   Пользователь не имеет соответствующих разрешений  
  
  
