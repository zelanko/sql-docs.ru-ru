---
title: Свойство FilterColumn (RDS) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FilterColumn property [ADO]
ms.assetid: 0a5473e8-8ce6-4518-83fb-4920b827e285
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 013511cbcb2455909a02b8c142f1dc15a7aa4b06
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="filtercolumn-property-rds"></a>Свойство FilterColumn (RDS)
Указывает столбец, в котором для оценки критериев фильтра.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.FilterColumn = String  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектную переменную, которая представляет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
 *Строковые значения*  
 Объект **строка** значение, указывающее столбец, в котором для оценки критериев фильтра. Указанные в критерии фильтра [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md) свойство.  
  
## <a name="remarks"></a>Замечания  
 [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), и **FilterColumn**свойства предоставляют сортировки и фильтрации функциональность на стороне клиента кэша. Функциональные возможности сортировки упорядочивает записи по значения из одного столбца. Функцию фильтра отображает подмножество записей на основе критериев поиска, при полной [записей](../../../ado/reference/ado-api/recordset-object-ado.md) сохраняется в кэше. [Сброс](../../../ado/reference/rds-api/reset-method-rds.md) метод будет выполнять критерии и заменить текущую **записей** с обновляемым **записей**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn, направления сортировки, свойства и пример метода сброса (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Свойство FilterCriterion (RDS)](../../../ado/reference/rds-api/filtercriterion-property-rds.md)   
 [Свойство FilterValue (RDS)](../../../ado/reference/rds-api/filtervalue-property-rds.md)   
 [Свойство SortColumn (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [Свойство SortDirection (служба удаленных рабочих столов)](../../../ado/reference/rds-api/sortdirection-property-rds.md)


