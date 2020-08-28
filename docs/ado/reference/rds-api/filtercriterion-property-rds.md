---
description: Свойство FilterCriterion (служба удаленных рабочих столов)
title: Свойство Филтеркритерион (RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FilterCriterion property [RDS]
ms.assetid: 24eb03ba-ccfd-4353-b6af-03586b2da6fd
author: rothja
ms.author: jroth
ms.openlocfilehash: faa4492693cd05828fc25a5ea7abcf8a763df3d9
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88982145"
---
# <a name="filtercriterion-property-rds"></a>Свойство FilterCriterion (служба удаленных рабочих столов)
Указывает оператор вычисления для использования в значении фильтра.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.FilterCriterion = String  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектная переменная, представляющая [RDS. Объект элемента управления](./datacontrol-object-rds.md) .  
  
 *String*  
 **Строковое** значение, указывающее оператор вычисления [FilterValue](./filtervalue-property-rds.md) для записей. Может быть одним из следующих: <, \<=, > , >=, = или <>.  
  
## <a name="remarks"></a>Remarks  
 Свойства [sortColumn](./sortcolumn-property-rds.md), [SortDirection](./sortdirection-property-rds.md), [FilterValue](./filtervalue-property-rds.md), **филтеркритерион**и [филтерколумн](./filtercolumn-property-rds.md) предоставляют функции сортировки и фильтрации кэша на стороне клиента. Функция сортировки упорядочивает записи по значениям из одного столбца. Функция фильтрации отображает подмножество записей на основе критериев поиска, а полный [набор записей](../ado-api/recordset-object-ado.md) сохраняется в кэше. Метод [Reset](./reset-method-rds.md) выполнит условия и заменит текущий **набор** записей на обновляемый **набор записей**.  
  
 Оператор "! =" недопустим для **филтеркритерион**; Вместо этого используйте "<>".  
  
 Если заданы оба свойства фильтрации и сортировки и вызван метод **Reset** , набор строк сначала фильтруется, а затем сортируется. Для сортировки по возрастанию значения NULL находятся вверху. для сортировки по убыванию значения NULL находятся внизу (поведение по умолчанию — по возрастанию).  
  
## <a name="applies-to"></a>Применение  
 [Объект DataControl (служба удаленных рабочих столов)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Филтерколумн, Филтеркритерион, FilterValue, SortColumn и SortDirection и метода Reset (VBScript)](./filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Свойство Филтерколумн (RDS)](./filtercolumn-property-rds.md)   
 [Свойство FilterValue (RDS)](./filtervalue-property-rds.md)   
 [Свойство SortColumn (RDS)](./sortcolumn-property-rds.md)   
 [Свойство SortDirection (служба удаленных рабочих столов)](./sortdirection-property-rds.md)