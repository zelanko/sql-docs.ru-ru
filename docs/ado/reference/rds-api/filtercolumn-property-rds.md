---
title: Свойство FilterColumn (служба удаленных рабочих СТОЛОВ) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FilterColumn property [ADO]
ms.assetid: 0a5473e8-8ce6-4518-83fb-4920b827e285
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73fa3e4631dac4e8f376a9832e1a1dbc0b753a52
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601972"
---
# <a name="filtercolumn-property-rds"></a>Свойство FilterColumn (служба удаленных рабочих столов)
Указывает столбец, для которого необходимо вычислить условия фильтра.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.FilterColumn = String  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектную переменную, которая представляет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
 *Строковые значения*  
 Объект **строка** значение, указывающее столбец, для которого необходимо вычислить условия фильтра. Условия фильтра указаны в [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md) свойство.  
  
## <a name="remarks"></a>Примечания  
 [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), и **FilterColumn**свойства предоставляют функций на стороне клиента кэша сортировки и фильтрации. Функция сортировки упорядочивает записей по значения одного столбца. Функция фильтрации отображается лишь часть записи на основе критерия поиска, при полной [записей](../../../ado/reference/ado-api/recordset-object-ado.md) сохраняется в кэше. [Сброс](../../../ado/reference/rds-api/reset-method-rds.md) метод будет выполнять критерии и замените текущую **записей** с обновляемый **записей**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn, SortDirection свойства и пример метода Reset (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Свойство FilterCriterion (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/filtercriterion-property-rds.md)   
 [Свойство FilterValue (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/filtervalue-property-rds.md)   
 [Свойство SortColumn (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [Свойство SortDirection (служба удаленных рабочих столов)](../../../ado/reference/rds-api/sortdirection-property-rds.md)


