---
title: Сравнение значений идентификатора GUID и uniqueidentifier
description: Здесь демонстрируется работа со значениями идентификатора GUID и uniqueidentifier в SQL Server и .NET.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 22d27f9a80765aacdfab25c568e8e2635f1779cc
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "78897018"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Сравнение значений идентификатора GUID и uniqueidentifier

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Тип данных глобального уникального идентификатора (GUID) в SQL Server представлен типом данных `uniqueidentifier`, который хранит 16-байтное двоичное значение. GUID — это двоичное число, которое используется в первую очередь как уникальный идентификатор в сети, в которой имеется много компьютеров на множестве сайтов. Идентификаторы GUID могут быть созданы путем вызова функции NEWID в Transact-SQL и гарантированно уникальны во всем мире. Дополнительные сведения см. в статье [uniqueidentifier (Transact-SQL)](../../../t-sql/data-types/uniqueidentifier-transact-sql.md).  
  
## <a name="working-with-sqlguid-values"></a>Работа со значениями SqlGuid  
Так как значения GUID являются длинными и сложными, для пользователей они не имеют смысла. Если случайно сгенерированные идентификаторы GUID используются для ключевых значений и вы вставляете большое количество строк, вы получаете случайные операции ввода-вывода в индексах, что может отрицательно сказаться на производительности. Идентификаторы GUID также относительно велики по сравнению с другими типами данных. В общем случае идентификаторы GUID рекомендуется использовать только в очень ограниченном круге ситуаций, когда ни один другой тип данных не подходит.  
  
### <a name="comparing-guid-values"></a>Сравнение значений GUID  
Значения `uniqueidentifier` поддерживают операторы сравнения, однако их упорядочивание реализовано без использования поразрядного сравнения. Над значениями `uniqueidentifier` можно выполнять только операции сравнения (=, <>, \<, >, \<=, >=), а также проверку на значение NULL (IS NULL и IS NOT NULL). Другие арифметические операторы не допускаются.  
  
Как <xref:System.Guid>, так и <xref:System.Data.SqlTypes.SqlGuid> содержат метод `CompareTo` для сравнения различных значений GUID. Однако `System.Guid.CompareTo` и `SqlTypes.SqlGuid.CompareTo` реализуются по-разному. <xref:System.Data.SqlTypes.SqlGuid> реализует `CompareTo`, используя поведение SQL Server, в последних шести байтах значения, которые являются наиболее значимыми. <xref:System.Guid> вычисляет все 16 байт. Это различие в поведении демонстрируется в следующем примере. В первом фрагменте кода показаны несортированные значения <xref:System.Guid>, а во втором фрагменте показаны отсортированные значения <xref:System.Guid>. В третьем фрагменте показаны отсортированные значения <xref:System.Data.SqlTypes.SqlGuid>. Выходные данные отображаются под листингом кода.  
  
[!code-csharp[DataWorks SqlGuid#1](~/../sqlclient/doc/samples/SqlGuid.cs#1)]
  
В примере получается следующий вывод.  
  
```console
Unsorted Guids:  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
  
Sorted Guids:  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
  
Sorted SqlGuids:  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
```  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Типы данных SQL Server и ADO.NET](sql-server-data-types.md)
