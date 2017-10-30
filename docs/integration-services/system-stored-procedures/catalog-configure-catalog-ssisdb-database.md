---
title: "Catalog.configure_catalog (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 72690c61-f462-4c25-9fce-08a687b0bd41
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 15bec231bf1de825cea952e07827074d56751386
ms.contentlocale: ru-ru
ms.lasthandoff: 10/20/2017

---
# <a name="catalogconfigurecatalog-ssisdb-database"></a>catalog.configure_catalog (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Настраивает каталог служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], задавая свойство каталога равным указанному значению.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql
catalog.configure_catalog [ @property_name = ] property_name , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @property_name =] *property_name*  
 Имя свойства каталога. *Property_name* — **nvarchar(255)**. Дополнительные сведения о доступных свойствах см. в разделе [catalog.catalog_properties &#40; База данных SSISDB &#41; ](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md).  
  
 [ @property_value =] *property_value*  
 Значение свойства каталога. *Property_value* — **nvarchar(255)**. Дополнительные сведения о значениях свойств см. в разделе [catalog.catalog_properties &#40; База данных SSISDB &#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md)  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Эта хранимая процедура определяет, является ли *property_value* является допустимым для каждого *property_name*.  
  
 Эта хранимая процедура может выполняться только в то время, когда не обрабатываются такие состояния, как «ожидание» (pending), «в очереди» (queued), «выполняется» (running) и «приостановлено» (paused).  
  
 Во время настройки каталога всех остальных хранимых процедур ошибкой с сообщением об ошибке «Сервер идет настройка.»
  
 Когда каталог настроен, в журнал операций заносится запись.  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Свойство не существует.  
  
-   Недопустимое значение свойства.  
  
  

