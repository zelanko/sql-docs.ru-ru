---
title: catalog.create_execution_dump | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 91319b0b-5536-4ab4-a403-9559ed9dd177
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c7db1abb55182116822eee78632b2046d45e88bd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811898"
---
# <a name="catalogcreateexecutiondump"></a>catalog.create_execution_dump
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Приводит к приостановке выполняемого пакета и создает файл дампа. Файл сохраняется в папке *\<диск>*:\Program Files\Microsoft SQL Server\130\Shared\ErrorDumps.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.create_execution_dump [ @execution_id = ] execution_id  
  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @execution_id = ] *execution_id*  
 Идентификатор выполнения для выполняющегося пакета. Параметр *execution_id* имеет тип **bigint**.  
  
## <a name="example"></a>Пример  
 В следующем примере выполняющийся пакет с идентификатором выполнения равным 88 получает запрос для создания файла дампа.  
  
```sql
EXEC create_execution_dump @execution_id = 88  
```  
  
## <a name="return-codes"></a>Коды возврата  
 0 (успешное завершение)  
  
 В случае отказа хранимой процедуры выдается ошибка.  
  
## <a name="result-set"></a>Результирующий набор  
 None  
  
## <a name="permissions"></a>Разрешения  
 Для этой хранимой процедуры требуется, чтобы пользователи были членами роли базы данных **ssis_admin**.  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке описываются условия, приводящие к сбою хранимой процедуры.  
  
-   Задан недопустимый идентификатор выполнения.  
  
-   Пакет уже завершен.  
  
-   В настоящее время пакет создает файл дампа.  
  
## <a name="see-also"></a>См. также:  
 [Создание файлов дампа для выполнения пакетов](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
