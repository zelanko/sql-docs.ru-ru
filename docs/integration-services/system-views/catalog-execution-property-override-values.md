---
title: catalog.execution_property_override_values | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 83cbdd6f-ddde-47bf-abde-36bd24272621
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 787baa21f2039647084b271a7cb63c681b6e7438
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35409836"
---
# <a name="catalogexecutionpropertyoverridevalues"></a>catalog.execution_property_override_values
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает значения переопределений свойств, заданные во время выполнения пакета.  
  
|Имя столбца|Тип данных|Описание|  
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
  
  
