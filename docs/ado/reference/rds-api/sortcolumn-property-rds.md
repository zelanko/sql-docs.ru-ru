---
description: Свойство SortColumn (служба удаленных рабочих столов)
title: Свойство SortColumn (RDS) | Документация Майкрософт
ms.technology: ado
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
ms.openlocfilehash: 62187b1643c315099d40d0bdd878699fcfc0065c
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724231"
---
# <a name="sortcolumn-property-rds"></a>Свойство SortColumn (служба удаленных рабочих столов)
Указывает, по какому столбцу следует отсортировать записи.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](/dotnet/framework/wcf/).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектная переменная, представляющая [RDS. Объект элемента управления](./datacontrol-object-rds.md) .  
  
 *String*  
 **Строковое** значение, представляющее имя или псевдоним столбца, по которому сортируются записи.  
  
## <a name="remarks"></a>Комментарии  
 Свойства **sortColumn**, [SortDirection](./sortdirection-property-rds.md), [FilterValue](./filtervalue-property-rds.md), [филтеркритерион](./filtercriterion-property-rds.md)и [филтерколумн](./filtercolumn-property-rds.md) предоставляют функции сортировки и фильтрации кэша на стороне клиента. Функция сортировки упорядочивает записи по значениям из одного столбца. Функция фильтрации отображает подмножество записей на основе критериев поиска, а полный [набор записей](../ado-api/recordset-object-ado.md) сохраняется в кэше. Метод [Reset](./reset-method-rds.md) выполнит условия и заменит текущий **набор** записей на обновляемый **набор записей**.  
  
 Чтобы выполнить сортировку по **набору записей**, необходимо сначала сохранить все ожидающие изменения. При использовании **RDS. Элемент управления**, можно использовать метод [SubmitChanges](./submitchanges-method-rds.md) . Например, если вы **RDS. Элемент управления** с именем ADC1, ваш код будет иметь вид `ADC1.SubmitChanges` . Если используется **набор записей**ADO, можно использовать его метод [UpdateBatch](../ado-api/updatebatch-method.md) . Использование **UpdateBatch** является рекомендуемым методом для объектов **набора записей** , созданных с помощью метода [CreateRecordset](./createrecordset-method-rds.md) . Например, код может быть `myRS.UpdateBatch` или `ADC1.Recordset.UpdateBatch` .  
  
## <a name="applies-to"></a>Применение  
 [Объект DataControl (служба удаленных рабочих столов)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Филтерколумн, Филтеркритерион, FilterValue, SortColumn и SortDirection и метода Reset (VBScript)](./filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort, свойство](../ado-api/sort-property.md)   
 [Свойство SortDirection (служба удаленных рабочих столов)](./sortdirection-property-rds.md)