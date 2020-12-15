---
title: Добавление существующих ограничений к набору данных DataSet
description: Описание процесса добавления существующих ограничений к набору данных DataSet.
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 9471f62c36604cb01ea78f558ac3bfbcb7f4bc01
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2020
ms.locfileid: "96772344"
---
# <a name="add-existing-constraints-to-a-dataset"></a>Добавление существующих ограничений к набору данных DataSet

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Метод <xref:System.Data.Common.DbDataAdapter.Fill%2A> объекта <xref:Microsoft.Data.SqlClient.SqlDataAdapter> заполняет <xref:System.Data.DataSet> только столбцами таблицы и строками из источника данных. Хотя источники данных обычно устанавливают ограничения, метод **Fill** по умолчанию не добавляет эти данные схемы к набору данных **DataSet**.

Чтобы учесть при заполнении набора данных **DataSet** существующие ограничения первичного ключа, заданные в источнике данных, можно вызвать метод <xref:System.Data.Common.DbDataAdapter.FillSchema%2A> объекта **DataAdapter** или задать значение свойства <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> объекта **DataAdapter**, равное **AddWithKey**, перед вызовом метода **Fill**. Тем самым ограничения первичного ключа в наборе данных **DataSet** будут соответствовать ограничениям первичного ключа в источнике данных.

> [!NOTE]
> Данные об ограничениях внешнего ключа не добавляются, их нужно создавать явно.

Добавление данных схемы в **DataSet** перед его заполнением обеспечивает включение ограничений первичного ключа в объекты <xref:System.Data.DataTable> набора данных **DataSet**. В результате при дополнительных вызовах для заполнения **DataSet** данные столбца первичного ключа используются для проверки соответствия новых строк из источника данных текущим строкам в каждой таблице **DataTable** и текущие данные таблиц перезаписываются данными из источника. При отсутствии данных схемы новые строки добавляются из источника данных к набору данных **DataSet**, что приводит к появлению повторяющихся строк.

> [!NOTE]
> Если столбец в источнике данных определен как столбец автоприращения, метод <xref:System.Data.Common.DbDataAdapter.FillSchema%2A> или <xref:System.Data.Common.DbDataAdapter.Fill%2A> со свойством <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A>, имеющим значение **AddWithKey**, создает столбец **DataColumn**, свойство которого **AutoIncrement** имеет значение `true`. Но выполнение задачи присваивания значений свойств **AutoIncrementStep** и **AutoIncrementSeed** необходимо взять на себя.

> [!NOTE]
> Использование метода **FillSchema** или присвоение свойству **MissingSchemaAction** значения **AddWithKey** требует дополнительной обработки в источнике данных, чтобы определить сведения о столбцах первичного ключа. Такая дополнительная обработка может снизить производительность. Если сведения о столбцах первичного ключа известны во время разработки, рекомендуется явно задавать столбец или столбцы первичного ключа, чтобы добиться оптимальной производительности.

В следующем примере кода показано добавление данных схемы в объект **DataSet** с помощью метода <xref:System.Data.Common.DbDataAdapter.FillSchema%2A>.

[!code-csharp[SqlDataAdapter_FillDataSet#1](~/../sqlclient/doc/samples/SqlDataAdapter_FillDataSet.cs#1)]

В следующем примере кода показано добавление данных схемы в объект **DataSet** с помощью свойства <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> и метода <xref:System.Data.Common.DbDataAdapter.Fill%2A>:

[!code-csharp[SqlDataAdapter_FillDataSet#2](~/../sqlclient/doc/samples/SqlDataAdapter_FillDataSet.cs#2)]

## <a name="handling-multiple-result-sets"></a>Обработка нескольких результирующих наборов

Если **DataAdapter** получит несколько результирующих наборов, возвращенных <xref:Microsoft.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, в наборе **DataSet** создается несколько таблиц. Эти таблицы по умолчанию получают имя **Table** *N* с последовательно увеличивающимся суффиксом, но начиная с **Table**, а не с "Table0". Если имя таблицы передается в качестве аргумента методу <xref:System.Data.Common.DbDataAdapter.FillSchema%2A>, то таблицы получают имя **TableName** *N* с отсчитываемым от нуля и последовательно увеличивающимся суффиксом, но начиная с **TableName**, а не с "TableName0".

## <a name="see-also"></a>См. также

- [Объекты DataAdapter и DataReader](dataadapters-datareaders.md)
- [Извлечение и изменение данных в ADO.NET](retrieving-modifying-data.md)
- [Microsoft ADO.NET для SQL Server](microsoft-ado-net-sql-server.md)
