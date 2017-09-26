---
title: "Catalog.rename_customized_logging_level | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b1a57d5e-3f03-4901-8b2b-bb8b371b595b
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 00c2cd8fa5f8423a7791d663d02aecbf27b8ab41
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogrenamecustomizedlogginglevel"></a>Catalog.rename_customized_logging_level
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Переименовывает существующий пользовательский уровень ведения журнала. Дополнительные сведения о пользовательских уровней ведения журнала см. в разделе [службы Integration Services &#40; Службы SSIS &#41; Ведение журнала](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```tsql  
rename_customized_logging_level [ @old_name = ] old_name  
    , [ @new_name = ] new_name  
  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @old_name =] *старое_имя*  
 Имя существующего пользовательский уровень ведения журнала для переименования.  
  
 *Старое_имя* — **nvarchar(128)**.  
  
 [ @new_name =] *новое_имя*  
 Новое имя для указанного пользовательский уровень ведения журнала.  
  
 *Новое_имя* — **nvarchar(128)**.  
  
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
  
  
