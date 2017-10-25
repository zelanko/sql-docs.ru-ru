---
title: "Catalog.create_execution_dump | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 91319b0b-5536-4ab4-a403-9559ed9dd177
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b05e1b46845c0a2b5ee47b94dc239d79d4a12a17
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcreateexecutiondump"></a>catalog.create_execution_dump
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Приводит к приостановке выполняемого пакета и создает файл дампа. Файл хранится в  *\<диска >*: папка \Program Files\Microsoft SQL Server\130\Shared\ErrorDumps.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.create_execution_dump [ @execution_id = ] execution_id  
  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @execution_id =] *execution_id*  
 Идентификатор выполнения для выполняющегося пакета. *Execution_id* — **bigint**.  
  
## <a name="example"></a>Пример  
 В следующем примере выполняющийся пакет с идентификатором выполнения равным 88 получает запрос для создания файла дампа.  
  
```sql
EXEC create_execution_dump @execution_id = 88  
```  
  
## <a name="return-codes"></a>Коды возврата  
 0 (успешное завершение)  
  
 В случае отказа хранимой процедуры выдается ошибка.  
  
## <a name="result-set"></a>Результирующий набор  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует от пользователей в качестве членов **ssis_admin** роли базы данных.  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке описываются условия, приводящие к сбою хранимой процедуры.  
  
-   Задан недопустимый идентификатор выполнения.  
  
-   Пакет уже завершен.  
  
-   В настоящее время пакет создает файл дампа.  
  
## <a name="see-also"></a>См. также:  
 [Создание файлов дампа для выполнения пакетов](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
