---
title: Сравнение значений идентификатора GUID и uniqueidentifier
description: Демонстрирует работу с GUID и значениями uniqueidentifier в SQL Server и .NET.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 8a4c5fcc63c2d2ddb8414227ea049e78db1cba10
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452279"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Сравнение значений идентификатора GUID и uniqueidentifier

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Тип данных глобального уникального идентификатора (GUID) в SQL Server представлен типом данных `uniqueidentifier`, который хранит 16-байтное двоичное значение. GUID — это двоичное число, а его основное использование — это идентификатор, который должен быть уникальным в сети, в которой имеется много компьютеров на многих сайтах. Идентификаторы GUID могут быть созданы путем вызова функции NEWID языка Transact-SQL и гарантированно уникальны во всем мире. Дополнительные сведения см. в разделе [uniqueidentifier (Transact-SQL)](../../../t-sql/data-types/uniqueidentifier-transact-sql.md).  
  
## <a name="working-with-sqlguid-values"></a>Работа со значениями Склгуид  
Так как значения GUID являются длинными и непонятными, они не имеют смысла для пользователей. Если для ключевых значений используются случайные идентификаторы GUID и вы вставляете большое количество строк, вы получаете случайные операции ввода-вывода в индексы, что может негативно сказаться на производительности. Идентификаторы GUID также относительно велики по сравнению с другими типами данных. В общем случае рекомендуется использовать идентификаторы GUID только для очень узких ситуаций, в которых не подходит ни один другой тип данных.  
  
### <a name="comparing-guid-values"></a>Сравнение значений GUID  
Значения `uniqueidentifier` поддерживают операторы сравнения, однако их упорядочивание реализовано без использования поразрядного сравнения. Над значениями `uniqueidentifier` можно выполнять только операции сравнения (=, <>, \<, >, \<=, >=), а также проверку на значение NULL (IS NULL и IS NOT NULL). Другие арифметические операторы не допускаются.  
  
Как <xref:System.Guid>, так и <xref:System.Data.SqlTypes.SqlGuid> имеют метод `CompareTo` для сравнения различных значений GUID. Однако `System.Guid.CompareTo` и `SqlTypes.SqlGuid.CompareTo` реализуются по-разному. <xref:System.Data.SqlTypes.SqlGuid> реализует `CompareTo` с помощью поведения SQL Server, в последних шести байтах значения являются наиболее значимыми. <xref:System.Guid> вычисляет все 16 байт. Это различие в поведении демонстрируется в следующем примере. В первом разделе кода отображаются несортированные <xref:System.Guid> значения, а во втором фрагменте кода показаны отсортированные значения <xref:System.Guid>. В третьем разделе показаны отсортированные <xref:System.Data.SqlTypes.SqlGuid> значения. Выходные данные отображаются под листингом кода.  
  
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
