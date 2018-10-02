---
title: catalog.deploy_packages | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 8e861df6-d103-4d84-8438-e822533f6849
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3416d7244d89a4cfe959ec8608f77d56fb20e0a0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47769552"
---
# <a name="catalogdeploypackages"></a>catalog.deploy_packages
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Развертывает один или несколько пакетов в папке каталога служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] или обновляет существующий пакет, который был развернут ранее.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
[catalog].[deploy_packages]     [ @folder_name = ] folder_name,    [ @project_name = ] project_name,    [ @packages_table = ] packages_table,     [ @operation_id OUTPUT ] operation_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name = ] *folder_name*  
 Имя папки. Параметр *folder_name* имеет тип **nvarchar(128)**.  
  
 [ @project_name = ] *project_name*  
 Имя проекта в папке. Параметр *project_name* имеет тип **nvarchar(128)**.  
  
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
  
  
