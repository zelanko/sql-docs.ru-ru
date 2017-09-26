---
title: "Catalog.deploy_packages | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 8e861df6-d103-4d84-8438-e822533f6849
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1839430dd7fb83ab16c4de46011819e3ce28e835
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogdeploypackages"></a>Catalog.deploy_packages
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Развертывание одного или нескольких пакетов в папке [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] каталога или обновление существующего пакета, который был развернут ранее.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[catalog].[deploy_packages]     [ @folder_name = ] folder_name,    [ @project_name = ] project_name,    [ @packages_table = ] packages_table,     [ @operation_id OUTPUT ] operation_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name =] *имя_папки*  
 Имя папки. *Имя_папки* — **nvarchar(128)**.  
  
 [ @project_name =] *project_name*  
 Имя проекта в папке. *Project_name* — **nvarchar(128)**.  
  
 [ @packages_table =] *packages_table*  
 Двоичное содержимое [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] пакета файлов (с расширением DTSX). *Packages_table* — **[catalog]. [ Package_Table_Type]**  
  
 [ @operation_id =] *operation_id*  
 Возвращает уникальный идентификатор для операции развертывания. *Operation_id* — **bigint**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения CREATE_OBJECTS на проект или изменить разрешения для пакета для обновления пакета.  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке приведено описание некоторых условий, при которых эта хранимая процедура может вызывать ошибки.  
  
-   Параметр ссылается на объект, который не существует, параметр пытается создать объект, который уже существует, или параметр недопустим, либо другим способом.  
  
-   У пользователя нет достаточных разрешений  
  
  
