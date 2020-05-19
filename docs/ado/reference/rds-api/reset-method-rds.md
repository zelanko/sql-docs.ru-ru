---
title: Метод Reset (RDS) | Документация Майкрософт
ms.technology: connectivity
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
ms.openlocfilehash: 9c2f40460a4690e32cb3f94963c8cbc1f7f06c15
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82750983"
---
# <a name="reset-method-rds"></a>Метод Reset (служба удаленных рабочих столов)
Выполняет сортировку или фильтрацию по **набору записей** на стороне клиента на основе указанных свойств сортировки и фильтра.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.Reset(value)  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектная переменная, представляющая [RDS. Объект элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *value*  
 Необязательный элемент. **Логическое** значение, равное **true** (по умолчанию), если необходимо выполнить фильтрацию по текущему набору строк с фильтрацией. **Значение false** указывает, что выполняется фильтрация по исходному набору строк, удаляя все предыдущие параметры фильтра.  
  
## <a name="remarks"></a>Примечания  
 Свойства [sortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [филтеркритерион](../../../ado/reference/rds-api/filtercriterion-property-rds.md)и [филтерколумн](../../../ado/reference/rds-api/filtercolumn-property-rds.md) предоставляют функции сортировки и фильтрации кэша на стороне клиента. Функция сортировки упорядочивает записи по значениям из одного столбца. Функция фильтрации отображает подмножество записей на основе условий поиска, а полный [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) сохраняется в кэше. Метод **Reset** выполнит условия и заменит текущий **набор** записей на обновляемый **набор записей**.  
  
 При наличии изменений в исходных данных, которые не были отправлены, метод **Reset** завершится ошибкой. Во-первых, используйте метод [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) для сохранения изменений в **наборе записей**для чтения и записи, а затем используйте метод **Reset** для сортировки или фильтрации записей.  
  
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
  
## <a name="applies-to"></a>Применяется к  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Филтерколумн, Филтеркритерион, FilterValue, SortColumn и SortDirection и метода Reset (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](../../../ado/reference/rds-api/submitchanges-method-rds.md)



