---
title: Сопоставления DataAdapter, DataTable и DataColumn
description: Описание настройки DataTableMappings и ColumnMappings для DataAdapter.
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: e8b2f84fbbf888fc67cdb8f945d7f0c887c14eaa
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2020
ms.locfileid: "96772323"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Сопоставления DataAdapter, DataTable и DataColumn

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Сопоставление <xref:Microsoft.Data.SqlClient.SqlDataAdapter> содержит коллекцию, имеющую от нуля или больше объектов <xref:System.Data.Common.DataTableMapping>, в своем свойстве <xref:System.Data.Common.DataAdapter.TableMappings%2A>. Класс **DataTableMapping** предоставляет главное сопоставление между данными, возвращенными запросом к источнику данных, и <xref:System.Data.DataTable>. Имя **DataTableMapping** может быть передано вместо имени **DataTable** в метод <xref:System.Data.Common.DbDataAdapter.Fill%2A> сопоставления **DataAdapter**. В следующем примере создается экземпляр класса **DataTableMapping** с именем **AuthorsMapping** для таблицы **Authors**.

```csharp
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");
```

Класс **DataTableMapping** позволяет использовать имена столбцов в объекте **DataTable**, отличные от таковых в базе данных. В сопоставлении **DataAdapter** это сопоставление используется для согласования столбцов при обновлении таблицы.

> [!NOTE]
> Если не указан объект **TableName** или имя **DataTableMapping** при вызове метода **Fill** или **Update** объекта **DataAdapter**, то в объекте **DataAdapter** выполняется поиск экземпляра **DataTableMapping** с именем "Table". Если имя **DataTableMapping** не существует, то значением **TableName** для объекта **DataTable** является "Table". Можно указать применяемый по умолчанию класс **DataTableMapping** при создании объекта **DataTableMapping** с именем "Table".

В следующем примере кода создается экземпляр **DataTableMapping** (из пространства имен <xref:System.Data.Common>) и задается в качестве применяемого по умолчанию отображения для указанного объекта **DataAdapter** путем присваивания ему имени "Table". Затем в этом примере столбцы из первой таблицы в результатах запроса (таблицы **Customers** базы данных **Northwind**) сопоставляются с набором понятных для пользователя имен в таблице **Northwind Customers** в <xref:System.Data.DataSet>. Для столбцов, к которым не применяется сопоставление, используются имена столбцов из источника данных.

[!code-csharp[SqlDataAdapter_TableMappings#1](~/../sqlclient/doc/samples/SqlDataAdapter_TableMappings.cs#1)]

В более сложных ситуациях может быть принято решение, что один и тот же экземпляр **DataAdapter** должен поддерживать загрузку разных таблиц с различными сопоставлениями. Чтобы обеспечить реализацию такого решения, достаточно ввести дополнительные объекты **DataTableMapping**.

Если методу **Fill** передается экземпляр **DataSet** и имя **DataTableMapping**, то при наличии сопоставления с этим именем используется это сопоставление; в противном случае используется объект **DataTable** с этим именем.

В следующих примерах создается экземпляр **DataTableMapping** с именем **Customers** и именем объекта **DataTable**, равным **BizTalkSchema**. Затем в этом примере строки, возвращаемые инструкцией SELECT, сопоставляются с объектом **DataTable**, имеющим имя **BizTalkSchema**.

[!code-csharp[SqlDataAdapter_TableMappings#2](~/../sqlclient/doc/samples/SqlDataAdapter_TableMappings.cs#2)]

> [!NOTE]
> Если для сопоставления столбцов не указано имя исходного столбца, будут автоматически созданы имена по умолчанию. Если ни один исходный столбец не предоставлен для сопоставления столбцов, то сопоставлению столбцов присваивается предусмотренное по умолчанию имя **SourceColumn** *N* с автоматически увеличивающимся суффиксом, начиная с **SourceColumn1**.

> [!NOTE]
> Если для сопоставления таблиц не указано имя исходной таблицы, будут автоматически созданы имена по умолчанию. Если ни одно имя исходной таблицы не предоставлено для сопоставления таблиц, то сопоставлению таблиц присваивается предусмотренное по умолчанию имя **SourceTable** *N* с автоматически увеличивающимся суффиксом, начиная с **SourceTable1**.

> [!NOTE]
> Рекомендуется избегать использования соглашения об именах **SourceColumn** *N* для сопоставления столбцов или **SourceTable** *N* для сопоставления таблиц, поскольку заданное имя может конфликтовать с существующим именем заданного по умолчанию сопоставления столбцов в коллекции **ColumnMappingCollection** или с именем сопоставления таблиц в коллекции **DataTableMappingCollection**. Если указанное имя уже существует, возникает исключение.

## <a name="handle-multiple-result-sets"></a>Обработка нескольких результирующих наборов

Если команда **SelectCommand** возвращает несколько таблиц, то в методе **Fill** для таблиц в объекте **DataSet** автоматически формируются имена, которые в качестве суффиксов имеют автоматически увеличивающиеся значения. Значения начинаются с указанного имени таблицы и увеличиваются в форме **TableName** *N*, первым значением является **TableName1**. Можно использовать сопоставления таблиц для сопоставления автоматически создаваемого имени таблицы с тем именем, которое требуется задать для таблицы в объекте **DataSet**. Например, для к команды **SelectCommand**, которая возвращает две таблицы, **Customers** и **Orders**, можно выполнить следующий вызов метода **Fill**.

```csharp
adapter.Fill(customersDataSet, "Customers");
```

В объекте **DataSet** будут созданы две таблицы: **Customers** и **Customers1**. Можно использовать сопоставления таблиц для обеспечения того, чтобы вторая таблица получила имя **Orders** вместо **Customers1**. Для этого необходимо сопоставить исходную таблицу **Customers1** с таблицей **Orders** из **DataSet**, как показано в следующем примере.

[!code-csharp[SqlDataAdapter_TableMappings#3](~/../sqlclient/doc/samples/SqlDataAdapter_TableMappings.cs#3)]

## <a name="see-also"></a>См. также

- [Объекты DataAdapter и DataReader](dataadapters-datareaders.md)
- [Извлечение и изменение данных в ADO.NET](retrieving-modifying-data.md)
- [Microsoft ADO.NET для SQL Server](microsoft-ado-net-sql-server.md)
