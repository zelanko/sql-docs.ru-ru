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
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 13ca11c107604c3da6d162b63a6d72ec6f76a201
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68007809"
---
# <a name="catalogdeployproject-ssisdb-database"></a>catalog.deploy_project (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Развертывает проект в папке каталога служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] или обновляет существующий проект, который был развернут ранее.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.deploy_project [@folder_name =] folder_name   
      , [@project_name =] project_name   
      , [@project_stream =] projectstream   
    [ , [@operation_id ] = operation_id OUTPUT ]   
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
  
-   Значение параметра *@project_name* не соответствует имени проекта в файле развертывания  
  
-   У пользователя нет достаточных разрешений  
  
## <a name="remarks"></a>Remarks  
 Во время развертывания или обновления проекта хранимая процедура не проверяет уровень защиты отдельных пакетов в проекте.  
  
  
