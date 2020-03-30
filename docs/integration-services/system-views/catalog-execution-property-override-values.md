---
title: catalog.execution_property_override_values | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 83cbdd6f-ddde-47bf-abde-36bd24272621
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5ad38c81101d983f70130bd0df5526ccba785f57
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "71296556"
---
# <a name="catalogexecution_property_override_values"></a>catalog.execution_property_override_values 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает значения переопределений свойств, заданные во время выполнения пакета.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|property_id|**bigint**|Уникальный идентификатор значения переопределения свойства.|  
|execution_id|**bigint**|Уникальный идентификатор для экземпляра исполнения.|  
|property_path|**nvarchar(4000)**|Путь к свойству в пакете.|  
|property_value|**nvarchar(max)**|Значение переопределения свойства.|  
|sensitive|**bit**|Если значение равно 1, свойство является конфиденциальным и шифруется при сохранении. Если значение равно 0, свойство не является конфиденциальным и его значение сохраняется в формате открытого текста.|  
  
## <a name="remarks"></a>Remarks  
 Это представление отображает по строке для каждого выполнения, в котором значения свойств были переопределены с помощью раздела **Переопределения свойств** вкладки **Расширенные** диалогового окна **Выполнение пакета**. Путь к свойству извлекается из свойства **Путь к пакету** задачи пакета.  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на экземпляр выполнения  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
