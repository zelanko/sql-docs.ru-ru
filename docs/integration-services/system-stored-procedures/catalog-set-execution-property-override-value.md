---
title: "Catalog.set_execution_property_override_value | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 37cb3c01-f4c0-4978-8e40-a975456def5a
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 20f2c882a78f5e60931b0152d5877898e1972d0a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetexecutionpropertyoverridevalue"></a>catalog.set_execution_property_override_value
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Задает значение свойства для экземпляра выполнения в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.set_execution_property_override_value [ @execution_id = execution_id  
    , [ @property_path = ] property_path  
    , [ @property_value = ] property_value  
    , [ @sensitive = ] sensitive  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @execution_id =] *execution_id*  
 Уникальный идентификатор для экземпляра выполнения. *Execution_id* — **bigint**.  
  
 [ @property_path =] *путь_к_свойству*  
 Путь к свойству в пакете. *Путь_к_свойству* — **nvarchar(4000)**.  
  
 [ @property_value =] *property_value*  
 Значение переопределения, присваиваемое свойству. *Property_value* — **nvarchar(max)**.  
  
 [ @sensitive =] *конфиденциальных*  
 Если значение равно 1, свойство является конфиденциальным и шифруется при сохранении. Если значение равно 0, свойство не является конфиденциальным и его значение сохраняется в формате открытого текста. *Конфиденциальных* аргумент **бит**.  
  
## <a name="remarks"></a>Замечания  
 Эта процедура выполняет ту же функцию, что **переопределяет свойство** статьи **Дополнительно** вкладке **выполнение пакета** диалогового окна. Путь к свойству является производным от **путь к пакету** свойства задачи пакета.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Пользователь не имеет соответствующих разрешений  
  
-   Недопустимый идентификатор выполнения  
  
-   Недопустимый путь к свойству  
  
-   Тип данных значения свойства не соответствует типу данных свойства  
  
## <a name="see-also"></a>См. также:  
 [catalog.set_execution_parameter_value (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
  
  

