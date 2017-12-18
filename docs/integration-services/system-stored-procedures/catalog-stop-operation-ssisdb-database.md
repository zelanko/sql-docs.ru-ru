---
title: "catalog.stop_operation (база данных SSISDB) | Документы Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 97fd9d22-03dd-4eda-8f6c-ba8b67acec68
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bf33675e591fbb16417bc3b251a1a47693b59673
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="catalogstopoperation-ssisdb-database"></a>catalog.stop_operation (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Останавливает проверку или экземпляр выполнения в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.stop_operation [ @operation_id = ] operation_id  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @operation_id = ] *operation_id*  
 Уникальный идентификатор проверки или экземпляра выполнения. Параметр *operation_id* имеет тип **bigint**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на проверку или экземпляр выполнения.  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Пользователь не имеет соответствующих разрешений  
  
-   Недопустимый идентификатор операции  
  
-   Операция уже остановлена  
  
## <a name="remarks"></a>Замечания  
 Только один пользователь за раз должен останавливать операцию в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Если несколько пользователей попытаются остановить операцию, хранимая процедура возвратит код успешного завершения при первой попытке (значение `0`), но последующие попытки будут приводить к ошибкам.  
  
  
