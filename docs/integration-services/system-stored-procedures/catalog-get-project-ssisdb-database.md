---
title: catalog.get_project (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: f263c9e4-a7db-4888-a458-70ae99b1f729
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 281e3d3a5c85e2c89991487c5c4988d0e1077ba6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635102"
---
# <a name="cataloggetproject-ssisdb-database"></a>catalog.get_project (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Получает двоичный поток проекта, развернутого на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.get_project [ @folder_name = ] folder_name , [ @project_name = ] project_name   
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name = ] *folder_name*  
 Имя папки, которая содержит проект. Параметр *folder_name* имеет тип **nvarchar(128)**.  
  
 [ @project_name = ] *project_name*  
 Имя проекта. Параметр *project_name* имеет тип **nvarchar(128)**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Двоичный поток проекта возвращается в виде объекта **varbinary(MAX)**. Если папка или проект не найдены, результат не возвращается.  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ на проект  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке перечислены некоторые условия, при которых хранимая процедура get_project может вызвать ошибку:  
  
-   Проект не существует  
  
-   Папка не существует  
  
-   Пользователь не имеет соответствующих разрешений  
  
  
