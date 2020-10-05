---
description: Метод Reset (служба удаленных рабочих столов)
title: Метод Reset (RDS) | Документация Майкрософт
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Reset method [ADO]
ms.assetid: 3957197a-f543-4d6b-9e11-67a77c2063b7
author: rothja
ms.author: jroth
ms.openlocfilehash: fcebd112b389fe98b69b25852ef0504e88890261
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724263"
---
# <a name="reset-method-rds"></a>Метод Reset (служба удаленных рабочих столов)
Выполняет сортировку или фильтрацию по **набору записей** на стороне клиента на основе указанных свойств сортировки и фильтра.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](/dotnet/framework/wcf/).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.Reset(value)  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектная переменная, представляющая [RDS. Объект элемента управления](./datacontrol-object-rds.md) .  
  
 *value*  
 Необязательный элемент. **Логическое** значение, равное **true** (по умолчанию), если необходимо выполнить фильтрацию по текущему набору строк с фильтрацией. **Значение false** указывает, что выполняется фильтрация по исходному набору строк, удаляя все предыдущие параметры фильтра.  
  
## <a name="remarks"></a>Комментарии  
 Свойства [sortColumn](./sortcolumn-property-rds.md), [SortDirection](./sortdirection-property-rds.md), [FilterValue](./filtervalue-property-rds.md), [филтеркритерион](./filtercriterion-property-rds.md)и [филтерколумн](./filtercolumn-property-rds.md) предоставляют функции сортировки и фильтрации кэша на стороне клиента. Функция сортировки упорядочивает записи по значениям из одного столбца. Функция фильтрации отображает подмножество записей на основе условий поиска, а полный [набор записей](../ado-api/recordset-object-ado.md) сохраняется в кэше. Метод **Reset** выполнит условия и заменит текущий **набор** записей на обновляемый **набор записей**.  
  
 При наличии изменений в исходных данных, которые не были отправлены, метод **Reset** завершится ошибкой. Во-первых, используйте метод [SubmitChanges](./submitchanges-method-rds.md) для сохранения изменений в **наборе записей**для чтения и записи, а затем используйте метод **Reset** для сортировки или фильтрации записей.  
  
 Если необходимо выполнить несколько фильтров для набора строк, можно использовать необязательный *логический* аргумент с методом **Reset** . В приведенном ниже примере показано, как это сделать.  
  
```  
ADC.SQL = "Select au_lname from authors"  
ADC.Refresh    ' Get the new rowset.  
  
ADC.FilterColumn = "au_lname"  
ADC.FilterCriterion = "<"  
ADC.FilterValue = "'M'"  
ADC.Reset         ' Rowset now has all Last Names < "M".  
  
ADC.FilterCriterion = ">"  
ADC.FilterValue = "'F'"  
' Passing True is not necessary, because it is the   
' default filter on the current "filtered" rowset.  
ADC.Reset(TRUE)     ' Rowset now has all Last   
                    ' Names < "M" and > "F".  
  
ADC.FilterCriterion = ">"  
ADC.FilterValue = "'T'"  
' Filter on the original rowset, throwing out the  
' previous filter options.  
ADC.Reset(FALSE)   ' Rowset now has all Last Names > "T".  
```  
  
## <a name="applies-to"></a>Применение  
 [Объект DataControl (служба удаленных рабочих столов)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Филтерколумн, Филтеркритерион, FilterValue, SortColumn и SortDirection и метода Reset (VBScript)](./filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](./submitchanges-method-rds.md)