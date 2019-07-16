---
title: Свойство SortColumn (служба удаленных рабочих СТОЛОВ) | Документация Майкрософт
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SortColumn property [RDS]
ms.assetid: f6f80f67-f0fb-4e63-a5f5-8fdf312aac63
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b5a9c3f9f50968f3b5e8085052917397bcd90226
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963397"
---
# <a name="sortcolumn-property-rds"></a>Свойство SortColumn (служба удаленных рабочих столов)
Указывает, какой столбец для сортировки записей.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектную переменную, которая представляет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
 *String*  
 Объект **строка** значение, представляющее имя или псевдоним столбца, по которому выполняется сортировка записей.  
  
## <a name="remarks"></a>Примечания  
 **SortColumn**, [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), и [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)свойства предоставляют функций на стороне клиента кэша сортировки и фильтрации. Функция сортировки упорядочивает записей по значения одного столбца. Функция фильтрации отображается лишь часть записи на основе критерия поиска, при полной [записей](../../../ado/reference/ado-api/recordset-object-ado.md) сохраняется в кэше. [Сброс](../../../ado/reference/rds-api/reset-method-rds.md) метод будет выполнять критерии и замените текущую **записей** с обновляемый **записей**.  
  
 Для сортировки **записей**, необходимо сначала сохранить все ожидающие изменения. Если вы используете **RDS. DataControl**, можно использовать [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) метод. Например если ваш **RDS. DataControl** — с именем ADC1, ваш код будет `ADC1.SubmitChanges`. Если вы используете ADO **записей**, можно использовать его [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод. С помощью **UpdateBatch** способ является предпочтительным для **записей** объекты, созданные с помощью [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) метод. Например, код может быть `myRS.UpdateBatch` или `ADC1.Recordset.UpdateBatch`.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn, SortDirection свойства и пример метода Reset (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Свойство сортировки](../../../ado/reference/ado-api/sort-property.md)   
 [Свойство SortDirection (служба удаленных рабочих столов)](../../../ado/reference/rds-api/sortdirection-property-rds.md)





