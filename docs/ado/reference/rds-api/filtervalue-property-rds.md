---
description: Свойство FilterValue (служба удаленных рабочих столов)
title: Свойство FilterValue (RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FilterValue property [ADO]
ms.assetid: 28f17186-b842-4cf9-b320-a9bb941c481b
author: rothja
ms.author: jroth
ms.openlocfilehash: b8e80ffc13f4c1bae1d668bb85317345288caa2c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438986"
---
# <a name="filtervalue-property-rds"></a>Свойство FilterValue (служба удаленных рабочих столов)
Указывает значение, с которым фильтруются записи.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.FilterValue = String  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектная переменная, представляющая [RDS. Объект элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *String*  
 **Строковое** значение, представляющее значение данных, с помощью которого отфильтруются записи (например, `'Programmer'` или `125` ).  
  
## <a name="remarks"></a>Remarks  
 Свойства [sortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), **FilterValue**, [филтеркритерион](../../../ado/reference/rds-api/filtercriterion-property-rds.md)и [филтерколумн](../../../ado/reference/rds-api/filtercolumn-property-rds.md) предоставляют функции сортировки и фильтрации кэша на стороне клиента. Функция сортировки упорядочивает записи по значениям из одного столбца. Функция фильтрации отображает подмножество записей на основе критериев поиска, а полный [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) сохраняется в кэше. Метод [Reset](../../../ado/reference/rds-api/reset-method-rds.md) выполнит условия и заменит текущий **набор** записей на обновляемый **набор записей**.  
  
 Значения NULL приводят к ошибке несоответствия типов.  
  
## <a name="applies-to"></a>Применение  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры свойств Филтерколумн, Филтеркритерион, FilterValue, SortColumn и SortDirection и метода Reset (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Свойство Филтерколумн (RDS)](../../../ado/reference/rds-api/filtercolumn-property-rds.md)   
 [Свойство Филтеркритерион (RDS)](../../../ado/reference/rds-api/filtercriterion-property-rds.md)   
 [Свойство SortColumn (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [Свойство SortDirection (служба удаленных рабочих столов)](../../../ado/reference/rds-api/sortdirection-property-rds.md)






















