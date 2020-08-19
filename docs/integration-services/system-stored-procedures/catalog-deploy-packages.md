---
description: catalog.deploy_packages
title: catalog.deploy_packages | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 8e861df6-d103-4d84-8438-e822533f6849
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 383fe8ab64e0488ded13726d83e80a8bf7244455
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422168"
---
# <a name="catalogdeploy_packages"></a>catalog.deploy_packages 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Развертывает один или несколько пакетов в папке каталога служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] или обновляет существующий пакет, который был развернут ранее.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.deploy_packages [ @folder_name = ] folder_name
    , [ @project_name = ] project_name
    , [ @packages_table = ] packages_table
    [, [ @operation_id OUTPUT = ] operation_id OUTPUT]
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name = ] *folder_name*  
 Имя папки. Параметр *folder_name* имеет тип **nvarchar(128)** .  
  
 [ @project_name = ] *project_name*  
 Имя проекта в папке. Параметр *project_name* имеет тип **nvarchar(128)** .  
  
 [ @packages_table = ] *packages_table*  
 Двоичное содержимое файлов (DTSX) пакета [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Параметр *packages_table* имеет тип **[catalog].[Package_Table_Type]**  
  
 [ @operation_id = ] *operation_id*  
 Возвращает уникальный идентификатор для операции развертывания. Параметр *operation_id* имеет тип **bigint**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения CREATE_OBJECTS на проект или разрешения MODIFY на пакет для обновления пакета.  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке приведено описание некоторых условий, при которых эта хранимая процедура может вызывать ошибки.  
  
-   Параметр ссылается на объект, который не существует, параметр пытается создать уже существующий объект или же параметр недопустим по какой-либо другой причине.  
  
-   У пользователя нет достаточных разрешений  
  
  
