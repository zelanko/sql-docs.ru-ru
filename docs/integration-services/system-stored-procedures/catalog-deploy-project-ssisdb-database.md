---
title: catalog.deploy_project (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 2e3439b4-7226-4b61-a993-7a1d161eac7e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b2578745d445c1f2ac91b037ac7ce8e694687a16
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86913050"
---
# <a name="catalogdeploy_project-ssisdb-database"></a>catalog.deploy_project (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Развертывает проект в папке каталога служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] или обновляет существующий проект, который был развернут ранее.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.deploy_project [@folder_name =] folder_name   
      , [ @project_name = ] project_name   
      , [ @project_stream = ] projectstream   
    [ , [ @operation_id = ] operation_id OUTPUT ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [@folder_name =] *folder_name*  
 Имя папки, в которой развертывается проект. Параметр *folder_name* имеет тип **nvarchar(128)** .  
  
 [@project_name =] *project_name*  
 Имя нового или обновленного проекта в папке. Параметр *project_name* имеет тип **nvarchar(128)** .  
  
 [@projectstream =] *projectstream*  
 Двоичное содержимое файла развертываний проекта служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (с расширением ISPAC).  
  
 Можно использовать инструкцию SELECT с функцией OPENROWSET и поставщиком больших наборов строк BULK для получения двоичного содержимого файла. Пример см. в разделе [Развертывание проектов и пакетов служб Integration Services (SSIS)](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md). Дополнительные сведения о предложении OPENROWSET см. в разделе [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md).  
  
 Параметр *projectstream* имеет тип **varbinary(MAX)**  
  
 [@operation_id =] *operation_id*  
 Возвращает уникальный идентификатор для операции развертывания. Параметр *operation_id* имеет тип **bigint**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения CREATE_OBJECTS на папку для развертывания нового проекта или разрешения MODIFY на проект для обновления проекта  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке приведено описание некоторых условий, при которых эта хранимая процедура может вызывать ошибки.  
  
-   Параметр ссылается на объект, который не существует, параметр пытается создать уже существующий объект или же параметр недопустим по какой-либо другой причине  
  
-   Значение параметра *\@project_name* не соответствует имени проекта в файле развертывания  
  
-   У пользователя нет достаточных разрешений  
  
## <a name="remarks"></a>Remarks  
 Во время развертывания или обновления проекта хранимая процедура не проверяет уровень защиты отдельных пакетов в проекте.  
  
  
