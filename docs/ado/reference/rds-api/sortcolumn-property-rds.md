---
title: "Свойство SortColumn (RDS) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: SortColumn property [RDS]
ms.assetid: f6f80f67-f0fb-4e63-a5f5-8fdf312aac63
caps.latest.revision: "18"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d8cdd4d854a4328613ab0fd98e8e107e207f2e12
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="sortcolumn-property-rds"></a>Свойство SortColumn (RDS)
Показывает, какой столбец для сортировки.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектную переменную, которая представляет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
 *Строковые значения*  
 Объект **строка** значение, представляющее имя или псевдоним столбца, по которому выполняется сортировка записей.  
  
## <a name="remarks"></a>Замечания  
 **SortColumn**, [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), и [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)свойства предоставляют сортировки и фильтрации функциональность на стороне клиента кэша. Функциональные возможности сортировки упорядочивает записи по значения из одного столбца. Функцию фильтра отображает подмножество записей на основе критериев поиска, при полной [записей](../../../ado/reference/ado-api/recordset-object-ado.md) сохраняется в кэше. [Сброс](../../../ado/reference/rds-api/reset-method-rds.md) метод будет выполнять критерии и заменить текущую **записей** с обновляемым **записей**.  
  
 Для сортировки **записей**, необходимо сначала сохранить ожидающие изменения. Если вы используете **RDS. DataControl**, можно использовать [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) метод. Например если ваш **RDS. DataControl** — с именем ADC1, код будет `ADC1.SubmitChanges`. При использовании ADO **записей**, можно использовать его [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод. С помощью **UpdateBatch** является рекомендуемым методом **записей** объекты, созданные с помощью [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) метод. Например, код может быть `myRS.UpdateBatch` или `ADC1.Recordset.UpdateBatch`.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также:  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn, направления сортировки, свойства и пример метода сброса (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Свойство сортировки](../../../ado/reference/ado-api/sort-property.md)   
 [Свойство SortDirection (служба удаленных рабочих столов)](../../../ado/reference/rds-api/sortdirection-property-rds.md)





