---
title: "Catalog.deploy_project (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 2e3439b4-7226-4b61-a993-7a1d161eac7e
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a2e3655bedbb24f2174a62c8792cd168e7642592
ms.openlocfilehash: 9871d26467a300119c742d398ff88f87825d930c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="catalogdeployproject-ssisdb-database"></a>catalog.deploy_project (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Развертывает проект в папке каталога служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] или обновляет существующий проект, который был развернут ранее.  
  
## <a name="syntax"></a>Синтаксис  
  
```tsql  
deploy_project [ @folder_name = ] folder_name   
      , [ @project_name = ] project_name   
      , [ @project_stream = ] projectstream   
    [ , [@operation_id ] = operation_id OUTPUT ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name =] *имя_папки*  
 Имя папки, в которой будет развернут проект. *Имя_папки* — **nvarchar(128)**.  
  
 [ @project_name =] *project_name*  
 Имя нового или обновленного проекта в папке. *Project_name* — **nvarchar(128)**.  
  
 [ @projectstream =] *projectstream*  
 Двоичное содержимое файла развертываний проекта служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (с расширением ISPAC).  
  
 Можно использовать инструкцию SELECT с функцией OPENROWSET и поставщиком больших наборов строк BULK для получения двоичного содержимого файла. Пример см. в разделе [развертывания Integration Services (SSIS) проектов и пакетов](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md). Дополнительные сведения о OPENROWSET см. в разделе [OPENROWSET &#40; Transact-SQL &#41; ](../../t-sql/functions/openrowset-transact-sql.md).  
  
 *Projectstream* — **varbinary(MAX)**  
  
 [ @operation_id =] *operation_id*  
 Возвращает уникальный идентификатор для операции развертывания. *Operation_id* — **bigint**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения CREATE_OBJECTS на папку для развертывания нового проекта или разрешения MODIFY на проект для обновления проекта  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке приведено описание некоторых условий, при которых эта хранимая процедура может вызывать ошибки.  
  
-   Параметр ссылается на объект, который не существует, параметр пытается создать уже существующий объект или же параметр недопустим по какой-либо другой причине  
  
-   Значение параметра  *@project_name*  не соответствует имени в файле развертывания проекта  
  
-   У пользователя нет достаточных разрешений  
  
## <a name="remarks"></a>Замечания  
 Во время развертывания или обновления проекта хранимая процедура не проверяет уровень защиты отдельных пакетов в проекте.  
  
  
