---
title: Свойство SortColumn (RDS) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 83975a46087f75d58be304c543f6e6a45b6db7e6
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82750839"
---
# <a name="sortcolumn-property-rds"></a>Свойство SortColumn (служба удаленных рабочих столов)
Указывает, по какому столбцу следует отсортировать записи.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектная переменная, представляющая [RDS. Объект элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *String*  
 **Строковое** значение, представляющее имя или псевдоним столбца, по которому сортируются записи.  
  
## <a name="remarks"></a>Remarks  
 Свойства **sortColumn**, [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [филтеркритерион](../../../ado/reference/rds-api/filtercriterion-property-rds.md)и [филтерколумн](../../../ado/reference/rds-api/filtercolumn-property-rds.md) предоставляют функции сортировки и фильтрации кэша на стороне клиента. Функция сортировки упорядочивает записи по значениям из одного столбца. Функция фильтрации отображает подмножество записей на основе критериев поиска, а полный [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) сохраняется в кэше. Метод [Reset](../../../ado/reference/rds-api/reset-method-rds.md) выполнит условия и заменит текущий **набор** записей на обновляемый **набор записей**.  
  
 Чтобы выполнить сортировку по **набору записей**, необходимо сначала сохранить все ожидающие изменения. При использовании **RDS. Элемент управления**, можно использовать метод [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) . Например, если вы **RDS. Элемент управления** с именем ADC1, ваш код будет иметь вид `ADC1.SubmitChanges` . Если используется **набор записей**ADO, можно использовать его метод [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) . Использование **UpdateBatch** является рекомендуемым методом для объектов **набора записей** , созданных с помощью метода [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) . Например, код может быть `myRS.UpdateBatch` или `ADC1.Recordset.UpdateBatch` .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Филтерколумн, Филтеркритерион, FilterValue, SortColumn и SortDirection и метода Reset (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort, свойство](../../../ado/reference/ado-api/sort-property.md)   
 [Свойство SortDirection (служба удаленных рабочих столов)](../../../ado/reference/rds-api/sortdirection-property-rds.md)





