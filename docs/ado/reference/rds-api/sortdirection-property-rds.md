---
title: Свойство SortDirection (служба удаленных рабочих СТОЛОВ) | Документация Майкрософт
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ef187cd2ae291413fccf10e2af51642c50e06e5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62670880"
---
# <a name="sortdirection-property-rds"></a>Свойство SortDirection (служба удаленных рабочих столов)
Указывает, ли порядок сортировки по возрастанию или по убыванию.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.SortDirection = value  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектную переменную, которая представляет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
 *Значение*  
 Объект **логическое** значение, которое, если значение **True**, указывает направление сортировки по возрастанию. **False** указывает порядок по убыванию.  
  
## <a name="remarks"></a>Примечания  
 [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), **SortDirection**, [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), и [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)свойства предоставляют функций на стороне клиента кэша сортировки и фильтрации. Функция сортировки упорядочивает записей с помощью значений из одного столбца. Функция фильтрации отображается лишь часть записи на основе критерия поиска, при полной [записей](../../../ado/reference/ado-api/recordset-object-ado.md) сохраняется в кэше. [Сброс](../../../ado/reference/rds-api/reset-method-rds.md) метод будет выполнять критерии и замените текущую **записей** с обновляемый **записей**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn, SortDirection свойства и пример метода Reset (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Свойство сортировки](../../../ado/reference/ado-api/sort-property.md)   
 [Свойство SortColumn (служба удаленных рабочих столов)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)


