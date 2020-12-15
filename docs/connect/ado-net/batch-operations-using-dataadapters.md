---
title: Пакетные операции с использованием объектов DataAdapter
description: Описание способа повышения производительности приложения за счет сокращения числа круговых путей в SQL Server при применении обновлений из набора данных DataSet.
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 1b720dff0678c68396fe7d8cf1f60f3ade70dd9d
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2020
ms.locfileid: "96772336"
---
# <a name="batch-operations-using-dataadapters"></a>Пакетные операции с использованием объектов DataAdapter

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Поддержка пакетных операций в ADO.NET позволяет объекту <xref:System.Data.Common.DataAdapter> группировать операции INSERT, UPDATE и DELETE из <xref:System.Data.DataSet> или <xref:System.Data.DataTable> к серверу вместо отправки за один раз одной операции. Уменьшение числа двусторонних передач сигнала на сервер обычно приводит к значительному повышению производительности. Пакетное обновление поддерживается поставщиком данных Microsoft SqlClient для SQL Server (<xref:Microsoft.Data.SqlClient>).

При обновлении базы данных изменениями из объекта <xref:System.Data.DataSet> в более ранних версиях ADO.NET метод `Update` для `DataAdapter` выполняет обновления в базе данных по одной строке. Когда он просматривает строки в указанной таблице <xref:System.Data.DataTable>, он проверяет каждую строку <xref:System.Data.DataRow>, чтобы выявить, не была ли она изменена. Если строка изменена, он вызывает соответствующую команду `UpdateCommand`, `InsertCommand` или `DeleteCommand` в зависимости от значения свойства <xref:System.Data.DataRow.RowState%2A> для этой строки. Каждое обновление строки подразумевает сетевую двустороннюю передачу сигнала в базу данных.

В поставщике данных Microsoft SqlClient для SQL Server класс <xref:Microsoft.Data.SqlClient.SqlDataAdapter> предоставляет свойство <xref:Microsoft.Data.SqlClient.SqlDataAdapter.UpdateBatchSize%2A>. При установке для свойства `UpdateBatchSize` положительного целого значения обновления базы данных посылаются как пакеты указанного размера. Например, при установке `UpdateBatchSize` в 10 производится группирование 10 отдельных инструкций и передача их как один пакет. При установке `UpdateBatchSize` в 0 <xref:Microsoft.Data.SqlClient.SqlDataAdapter> использует самой большой размер пакета, который может обработать сервер. При его установке в 1 отключаются пакетные обновления, т. к. строки посылаются по одной.

> [!NOTE]
> Выполнение очень больших пакетов может снизить производительность. Поэтому необходимо экспериментальным путем найти параметр оптимального размера пакета перед реализацией приложения.

## <a name="use-the-updatebatchsize-property"></a>Использование свойства UpdateBatchSize

Если пакетные обновления включены, значение свойства <xref:System.Data.IDbCommand.UpdatedRowSource%2A> для `UpdateCommand`, `InsertCommand` и `DeleteCommand` объекта DataAdapter должно быть установлено в <xref:System.Data.UpdateRowSource.None> или <xref:System.Data.UpdateRowSource.OutputParameters>. При выполнении пакетного обновления значение свойства <xref:System.Data.IDbCommand.UpdatedRowSource%2A> команды для <xref:System.Data.UpdateRowSource.FirstReturnedRecord> или <xref:System.Data.UpdateRowSource.Both> недействительно.
  
Следующая процедура демонстрирует использование свойства `UpdateBatchSize`. Процедура принимает два аргумента, объект <xref:System.Data.DataSet>, который имеет столбцы, представляющие поля **ProductCategoryID** и **Name** в таблице **Production.ProductCategory**, и целое число, представляющее размер пакета (число строк в пакете). Код создает новый объект <xref:Microsoft.Data.SqlClient.SqlDataAdapter>, устанавливая его свойства <xref:Microsoft.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:Microsoft.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> и <xref:Microsoft.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A>. В коде предполагается, что объект <xref:System.Data.DataSet> имеет измененные строки. В нем устанавливается свойство `UpdateBatchSize` и выполняется обновление.

[!code-csharp[SqlDataAdapter_Batch#1](~/../sqlclient/doc/samples/SqlDataAdapter_Batch.cs#1)]

## <a name="handle-batch-update-related-events-and-errors"></a>Обработка событий и ошибок, связанных с пакетным обновлением

Объект **DataAdapter** имеет два события, связанных с обновлением: **RowUpdating** и **RowUpdated**. Дополнительные сведения см. в разделе [Обработка событий DataAdapter](handle-dataadapter-events.md).

### <a name="event-behavior-changes-with-batch-updates"></a>Изменения в поведении событий при работе с пакетными обновлениями

Если пакетное обновление включено, несколько строк обновляются одной операцией базы данных. Поэтому для каждого пакета происходит только одно событие `RowUpdated`, в то время как событие `RowUpdating` происходит для каждой обрабатываемой строки. Если пакетное обновление отключено, два события инициируются с чередованием один к одному, где одно событие `RowUpdating` и одно событие `RowUpdated` инициируется для строки, а затем одно событие `RowUpdating` и одно событие `RowUpdated` инициируются для следующей строки, до тех пор пока не будут обработаны все строки.

### <a name="access-updated-rows"></a>Доступ к обновленным строкам

Если пакетная обработка отключена, доступ к обновляемой строке может быть выполнен при помощи свойства <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> класса <xref:System.Data.Common.RowUpdatedEventArgs>.

Если пакетная обработка включена для нескольких строк, формируется одно событие `RowUpdated`. Поэтому значение свойства `Row` для каждой из строк равно NULL. События `RowUpdating` по-прежнему вызываются для каждой строки. Метод <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> класса <xref:System.Data.Common.RowUpdatedEventArgs> позволяет обращаться к обработанным строкам, копируя ссылки на строки в массив. Если строки не обрабатываются, метод `CopyToRows` инициирует исключение <xref:System.ArgumentNullException>. Свойство <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> используется для возврата числа строк, обработанных перед вызовом метода <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A>.

### <a name="handle-data-errors"></a>Обработка ошибок данных

Пакетное выполнение оказывает то же влияние, что и выполнение каждой отдельной инструкции. Инструкции выполняются в порядке, который инструкции добавили в пакет. Ошибки обрабатываются в пакетном режиме, как если было бы при отключении пакетного режима. Каждая строка обрабатывается отдельно. Только успешно обработанные в базе данных строки будут обновлены в соответствующей строке <xref:System.Data.DataRow> таблицы <xref:System.Data.DataTable>.

> [!NOTE]
> Поставщик данных Microsoft SqlClient для SQL Server и внутренний сервер базы данных определяют, какие конструкции SQL поддерживаются для пакетного выполнения. Если неподдерживаемая инструкция подается на выполнение, создается исключение.

## <a name="see-also"></a>См. также

- [Объекты DataAdapter и DataReader](dataadapters-datareaders.md)
- [Обновление источников данных с помощью DataAdapter](update-data-sources-with-dataadapters.md)
- [Обработка событий DataAdapter](handle-dataadapter-events.md)
- [Microsoft ADO.NET для SQL Server](microsoft-ado-net-sql-server.md)
