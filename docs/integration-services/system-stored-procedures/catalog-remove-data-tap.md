---
title: "catalog.remove_data_tap | Документы Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b77db3e6-478c-441a-a838-82c4de750275
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 28339c0762182397a266fa42abf6411a3dd56ef4
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="catalogremovedatatap"></a>catalog.remove_data_tap
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Удаляет отвод данных с выхода компонента, находящегося в выполнении. Уникальный идентификатор отвода данных связывается с экземпляром выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.remove_data_tap [ @data_tap_id = ] data_tap_id  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @data_tap_id = ] *data_tap_id*  
 Уникальный идентификатор отвода данных, созданного с использованием хранимой процедуры catalog.add_data_tap. Параметр *data_tap_id* имеет тип **bigint**.  
  
## <a name="remarks"></a>Замечания  
 Если пакет содержит более одной задачи потока данных с одинаковым именем, отвод данных добавляется к первой задаче потока данных с таким именем.  
  
## <a name="return-codes"></a>Коды возврата  
 0 (успешное завершение)  
  
 В случае отказа хранимой процедуры выдается ошибка.  
  
## <a name="result-set"></a>Результирующий набор  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Чтобы удалить отводы данных, экземпляр выполнения должен быть создан (значение 1 в столбце **status** представления [catalog.operations (база данных SSISDB)](../../integration-services/system-views/catalog-operations-ssisdb-database.md)).  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения MODIFY на экземпляр выполнения  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке описываются условия, приводящие к сбою хранимой процедуры.  
  
-   Пользователь не имеет разрешений MODIFY.  
  
## <a name="see-also"></a>См. также:  
 [catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)   
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
  
  
