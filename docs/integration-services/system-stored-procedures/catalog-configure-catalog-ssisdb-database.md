---
title: catalog.configure_catalog (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 72690c61-f462-4c25-9fce-08a687b0bd41
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4e8da4de862bf67a552da61a5d921e7c6c4c51fa
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71281350"
---
# <a name="catalogconfigure_catalog-ssisdb-database"></a>catalog.configure_catalog (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Настраивает каталог служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], задавая свойство каталога равным указанному значению.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql
catalog.configure_catalog [ @property_name = ] property_name , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @property_name = ] *property_name*  
 Имя свойства каталога. Параметр *property_name* имеет тип **nvarchar(255)** . Дополнительные сведения о доступных свойствах см. в разделе [catalog.catalog_properties (база данных SSISDB)](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md).  
  
 [ @property_value = ] *property_value*  
 Значение свойства каталога. Параметр *property_value* имеет тип **nvarchar(255)** . Дополнительные сведения о значениях свойств см. в разделе [catalog.catalog_properties (база данных SSISDB)](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md)  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Эта хранимая процедура определяет, действительно ли значение *property_value* для каждого *property_name*.  
  
 Эта хранимая процедура может выполняться только в то время, когда не обрабатываются такие состояния, как «ожидание» (pending), «в очереди» (queued), «выполняется» (running) и «приостановлено» (paused).  
  
 Когда настраивается каталог, при попытке выполнения всех остальных хранимых процедур выдается сообщение об ошибке "Идет настройка сервера".
  
 Когда каталог настроен, в журнал операций заносится запись.  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Свойство не существует.  
  
-   Недопустимое значение свойства.  
  
  
