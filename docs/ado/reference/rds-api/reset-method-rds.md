---
title: "Reset-метод (RDS) | Документы Microsoft"
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: Reset method [ADO]
ms.assetid: 3957197a-f543-4d6b-9e11-67a77c2063b7
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef5dfc619f39547150d096721da70c0ac715d04d
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2017
---
# <a name="reset-method-rds"></a>Метод Reset (RDS)
Выполняет сортировки или фильтрации на стороне клиента **записей** на основе указанного свойств сортировки и фильтрации.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.Reset(value)  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектную переменную, которая представляет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
 *value*  
 Необязательный параметр. Объект **логическое** значение, равное **True** (по умолчанию), если нужно выполнить фильтрацию в текущем наборе строк «фильтрация». **False** указывает, что отфильтровать на первоначальный набор строк, удаляя все предыдущие параметры фильтра.  
  
## <a name="remarks"></a>Remarks  
 [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), и [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)свойства предоставляют сортировки и фильтрации функциональность на стороне клиента кэша. Функциональные возможности сортировки упорядочивает записи по значения из одного столбца. Функцию фильтра отображает подмножество записей на основе критерия поиска, при полной [записей](../../../ado/reference/ado-api/recordset-object-ado.md) сохраняется в кэше. **Сброс** метод будет выполнять критерии и заменить текущую **записей** с обновляемым **записей**.  
  
 При внесении изменений в исходных данных, которые не были отправлены, **Сброс** метод завершится с ошибкой. Во-первых, используйте [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) метод, чтобы сохранить изменения в чтение и запись **записей**и затем использовать **Сброс** метод сортировки и фильтрации записей.  
  
 Если вы хотите выполнить более одного фильтра для набора строк, можно использовать необязательный *логическое* аргумент с **Сброс** метод. Следующий пример показывает, как это сделать:  
  
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
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также:  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn, направления сортировки, свойства и пример метода сброса (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](../../../ado/reference/rds-api/submitchanges-method-rds.md)



