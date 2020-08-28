---
description: Свойство SortDirection (служба удаленных рабочих столов)
title: Свойство SortDirection (RDS) | Документация Майкрософт
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SortDirection property [RDS]
ms.assetid: 1d9d8715-e4ad-4ff3-bf7f-f1dc0532d8c2
author: rothja
ms.author: jroth
ms.openlocfilehash: aa7bdefd98c908ed97b225ebe268b33f353b5042
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88981145"
---
# <a name="sortdirection-property-rds"></a>Свойство SortDirection (служба удаленных рабочих столов)
Указывает, используется ли порядок сортировки по возрастанию или по убыванию.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.SortDirection = value  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектная переменная, представляющая [RDS. Объект элемента управления](./datacontrol-object-rds.md) .  
  
 *Значение*  
 **Логическое** значение, которое при установке значения **true**указывает направление сортировки по возрастанию. **Значение false** указывает на убывающий порядок.  
  
## <a name="remarks"></a>Remarks  
 Свойства [sortColumn](./sortcolumn-property-rds.md), **SortDirection**, [FilterValue](./filtervalue-property-rds.md), [филтеркритерион](./filtercriterion-property-rds.md)и [филтерколумн](./filtercolumn-property-rds.md) предоставляют функции сортировки и фильтрации кэша на стороне клиента. Функция сортировки упорядочивает записи, используя значения из одного столбца. Функция фильтрации отображает подмножество записей на основе критериев поиска, а полный [набор записей](../ado-api/recordset-object-ado.md) сохраняется в кэше. Метод [Reset](./reset-method-rds.md) выполнит условия и заменит текущий **набор** записей на обновляемый **набор записей**.  
  
## <a name="applies-to"></a>Применение  
 [Объект DataControl (служба удаленных рабочих столов)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Филтерколумн, Филтеркритерион, FilterValue, SortColumn и SortDirection и метода Reset (VBScript)](./filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort, свойство](../ado-api/sort-property.md)   
 [Свойство SortColumn (служба удаленных рабочих столов)](./sortcolumn-property-rds.md)