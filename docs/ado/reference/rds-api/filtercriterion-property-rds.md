---
title: Свойство FilterCriterion (служба удаленных рабочих СТОЛОВ) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f3c45059eb0ed2599a25623f7e5f88946778429c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730342"
---
# <a name="filtercriterion-property-rds"></a>Свойство FilterCriterion (служба удаленных рабочих столов)
Указывает оператор вычисления использовать значения фильтра.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.FilterCriterion = String  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектную переменную, которая представляет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
 *Строковые значения*  
 Объект **строка** значение, которое указывает оператор оценки [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md) к записям. Может принимать одно из следующих: <, \<=, >, > =, =, или <>.  
  
## <a name="remarks"></a>Примечания  
 [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), **FilterCriterion**, и [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)свойства предоставляют функций на стороне клиента кэша сортировки и фильтрации. Функция сортировки упорядочивает записей по значения одного столбца. Функция фильтрации отображается лишь часть записи на основе критерия поиска, при полной [записей](../../../ado/reference/ado-api/recordset-object-ado.md) сохраняется в кэше. [Сброс](../../../ado/reference/rds-api/reset-method-rds.md) метод будет выполнять критерии и замените текущую **записей** с обновляемый **записей**.  
  
 «! =» Недопустимый оператор для **FilterCriterion**; вместо этого используйте «<>».  
  
 Если сортировка и фильтр свойств и вызове **Сброс** метод, набор строк сначала фильтруется и затем будет выполняться сортировка. Для сортировки в порядке возрастания, пустые значения отображаются в верхней части; для Сортировка по убыванию значения null, в нижней (по возрастанию — поведение по умолчанию).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn, SortDirection свойства и пример метода Reset (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Свойство FilterColumn (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/filtercolumn-property-rds.md)   
 [Свойство FilterValue (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/filtervalue-property-rds.md)   
 [Свойство SortColumn (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [Свойство SortDirection (служба удаленных рабочих столов)](../../../ado/reference/rds-api/sortdirection-property-rds.md)


