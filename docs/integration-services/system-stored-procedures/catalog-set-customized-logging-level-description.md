---
title: "Catalog.set_customized_logging_level_description | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 6ceaa39f-2439-457b-b99f-f12d88a1be32
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3899e02c6b1eaa2cc76ad4411d9be3aded817728
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetcustomizedloggingleveldescription"></a>Catalog.set_customized_logging_level_description
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Изменяет описание существующий пользовательский уровень ведения журнала. Дополнительные сведения о пользовательских уровней ведения журнала см. в разделе [службы Integration Services &#40; Службы SSIS &#41; Ведение журнала](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.set_customized_logging_level_description [ @level_name = ] level_name  
    , [ @level_description = ] level_description  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @level_name =] *level_name*  
 Имя существующего пользовательский уровень ведения журнала.  
  
 *Level_name* — **nvarchar(128)**.  
  
 [ @level_description =] *level_description*  
 Новое описание для указанного пользовательский уровень ведения журнала.  
  
 *Level_description* — **nvarchar(1024)**.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="return-codes"></a>Коды возврата  
 0 (успешное завершение)  
  
 В случае отказа хранимой процедуры выдается ошибка.  
  
## <a name="result-set"></a>Результирующий набор  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке описываются условия, приводящие к сбою хранимой процедуры.  
  
-   Пользователь не имеет необходимых разрешений.  
  
  

