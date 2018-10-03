---
title: catalog.set_customized_logging_level_description | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 6ceaa39f-2439-457b-b99f-f12d88a1be32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bc81bf11ef47c5a22f67547f32eeeca0ed93b5a3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47653581"
---
# <a name="catalogsetcustomizedloggingleveldescription"></a>catalog.set_customized_logging_level_description
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Изменяет описание существующего настроенного уровня ведения журнала. Дополнительные сведения о настроенных уровнях ведения журналов см. в разделе [Ведение журналов в службах Integration Services (SSIS)](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.set_customized_logging_level_description [ @level_name = ] level_name  
    , [ @level_description = ] level_description  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @level_name = ] *level_name*  
 Название существующего настроенного уровня ведения журнала.  
  
 Параметр *level_name* имеет тип **nvarchar(128)**.  
  
 [ @level_description = ] *level_description*  
 Новое описание указанного настроенного уровня ведения журнала.  
  
 Параметр *level_description* имеет тип **nvarchar(1024)**.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="return-codes"></a>Коды возврата  
 0 (успешное завершение)  
  
 В случае отказа хранимой процедуры выдается ошибка.  
  
## <a name="result-set"></a>Результирующий набор  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке описываются условия, приводящие к сбою хранимой процедуры.  
  
-   У пользователя отсутствуют необходимые разрешения.  
  
  
