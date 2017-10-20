---
title: "Catalog.remove_data_tap | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b77db3e6-478c-441a-a838-82c4de750275
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2f2c9b5d9333c201120e5f3a3e392c59012a8ac7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogremovedatatap"></a>catalog.remove_data_tap
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Удаляет отвод данных с выхода компонента, находящегося в выполнении. Уникальный идентификатор отвода данных связывается с экземпляром выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.remove_data_tap [ @data_tap_id = ] data_tap_id  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @data_tap_id =] *data_tap_id*  
 Уникальный идентификатор отвода данных, созданного с использованием хранимой процедуры catalog.add_data_tap. *Data_tap_id* — **bigint**.  
  
## <a name="remarks"></a>Замечания  
 Если пакет содержит более одной задачи потока данных с одинаковым именем, отвод данных добавляется к первой задаче потока данных с таким именем.  
  
## <a name="return-codes"></a>Коды возврата  
 0 (успешное завершение)  
  
 В случае отказа хранимой процедуры выдается ошибка.  
  
## <a name="result-set"></a>Результирующий набор  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Чтобы удалить отводы данных, экземпляр выполнения должен быть создан (значение 1 в **состояние** столбец [catalog.operations &#40; База данных SSISDB &#41; ](../../integration-services/system-views/catalog-operations-ssisdb-database.md)представления).  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения MODIFY на экземпляр выполнения  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке описываются условия, приводящие к сбою хранимой процедуры.  
  
-   Пользователь не имеет разрешений MODIFY.  
  
## <a name="see-also"></a>См. также:  
 [Catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)   
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
  
  
