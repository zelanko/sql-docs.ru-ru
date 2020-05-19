---
title: Свойство Филтеркритерион (RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: 88e1bbdb45b48e42d69bd921384056089b3a2241
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82752028"
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
 Объектная переменная, представляющая [RDS. Объект элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *String*  
 **Строковое** значение, указывающее оператор вычисления [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md) для записей. Может принимать одно из следующих действий: <, \< =, >, >=, = или <>.  
  
## <a name="remarks"></a>Примечания  
 Свойства [sortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), **филтеркритерион**и [филтерколумн](../../../ado/reference/rds-api/filtercolumn-property-rds.md) предоставляют функции сортировки и фильтрации кэша на стороне клиента. Функция сортировки упорядочивает записи по значениям из одного столбца. Функция фильтрации отображает подмножество записей на основе критериев поиска, а полный [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) сохраняется в кэше. Метод [Reset](../../../ado/reference/rds-api/reset-method-rds.md) выполнит условия и заменит текущий **набор** записей на обновляемый **набор записей**.  
  
 Оператор "! =" недопустим для **филтеркритерион**; Вместо этого используйте "<>".  
  
 Если заданы оба свойства фильтрации и сортировки и вызван метод **Reset** , набор строк сначала фильтруется, а затем сортируется. Для сортировки по возрастанию значения NULL находятся вверху. для сортировки по убыванию значения NULL находятся внизу (поведение по умолчанию — по возрастанию).  
  
## <a name="applies-to"></a>Применяется к  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Филтерколумн, Филтеркритерион, FilterValue, SortColumn и SortDirection и метода Reset (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Свойство Филтерколумн (RDS)](../../../ado/reference/rds-api/filtercolumn-property-rds.md)   
 [Свойство FilterValue (RDS)](../../../ado/reference/rds-api/filtervalue-property-rds.md)   
 [Свойство SortColumn (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [Свойство SortDirection (служба удаленных рабочих столов)](../../../ado/reference/rds-api/sortdirection-property-rds.md)


