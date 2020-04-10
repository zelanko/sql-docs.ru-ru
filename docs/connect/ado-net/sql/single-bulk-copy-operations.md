---
title: Одинарные операции массового копирования
description: Описание процессов одного массового копирования данных в экземпляр SQL Server с помощью класса SqlBulkCopy, а также массового копирования с помощью инструкций Transact-SQL и класса SqlCommand.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 1553e736115eb75769f80d9f5001aecb0e855792
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925452"
---
# <a name="single-bulk-copy-operations"></a>Одинарные операции массового копирования

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Самый простой способ массового копирования SQL Server — выполнение одной операции в базе данных. По умолчанию операция массового копирования выполняется как изолированная, т. е. не как транзакция и без возможности отката.  
  
> [!NOTE]
>  Если при возникновении ошибки необходимо частично или полностью отменить массовое копирование, можно использовать управляемую <xref:Microsoft.Data.SqlClient.SqlBulkCopy> транзакцию или выполнить операцию массового копирования в существующей транзакции. **SqlBulkCopy** также будет работать с <xref:System.Transactions>, если это соединение прикреплено (явно или неявно) к транзакции **System.Transactions**.  
>   
>  Дополнительные сведения см. в статье [Транзакции и операции массового копирования](transaction-bulk-copy-operations.md).  
  
Для массового копирования выполните описанную ниже процедуру.  
  
1. Подключитесь к исходному серверу и получите данные для копирования. Данные также могут поступать из других источников, если их можно извлечь из объекта <xref:System.Data.IDataReader> или <xref:System.Data.DataTable>.  
  
2. Подключитесь к целевому серверу (если только не требуется, чтобы объект **SqlBulkCopy** сам установил соединение).  
  
3. Создайте объект <xref:Microsoft.Data.SqlClient.SqlBulkCopy>, задав все необходимые свойства.  
  
4. Задайте свойство **DestinationTableName**, чтобы указать целевую таблицу для операции массовой вставки.  
  
5. Вызовите один из методов **WriteToServer**.  
  
6. Кроме того, если это необходимо, можно обновить свойства и вызвать метод **WriteToServer**.  
  
7. Вызовите <xref:Microsoft.Data.SqlClient.SqlBulkCopy.Close%2A> или заключите код операций массового копирования в инструкцию `Using`.  
  
> [!CAUTION]
>  Мы рекомендуем, чтобы исходные и целевые типы данных столбцов совпадали. Если типы данных разные, объект **SqlBulkCopy** попытается преобразовать каждое исходное значение в целевой тип данных с использованием правил, применяемых методом <xref:Microsoft.Data.SqlClient.SqlParameter.Value%2A>. Преобразование может повлиять на производительность и может привести к непредвиденным ошибкам. Например, в большинстве случаев тип данных `Double` может преобразовываться в тип данных `Decimal`, но это происходит не всегда.  
  
## <a name="example"></a>Пример  
Следующее консольное приложение показывает, как загрузить данные с помощью класса <xref:Microsoft.Data.SqlClient.SqlBulkCopy>. В этом примере объект <xref:Microsoft.Data.SqlClient.SqlDataReader> используется, чтобы скопировать данные из таблицы **Production.Product** в базе данных SQL Server **AdventureWorks** в такую же таблицу в этой же базе данных.  
  
> [!IMPORTANT]
>  Этот пример не будет работать, если вы не создали рабочие таблицы, как описано в разделе [Пример настройки массового копирования](bulk-copy-example-setup.md). Этот код предназначен только для демонстрации синтаксиса использования **SqlBulkCopy**. Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL `INSERT … SELECT` для копирования данных.  
  
[!code-csharp[DataWorks SqlBulkCopy_WriteToServer#1](~/../sqlclient/doc/samples/SqlBulkCopy_WriteToServer.cs#1)]
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Выполнение операции массового копирования с помощью Transact-SQL и класса command  
Следующий пример демонстрирует использование метода <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> для выполнения инструкции BULK INSERT.  
  
> [!NOTE]
>  Путь к источнику данных указан относительно сервера. Для успешного выполнения массового копирования у процесса сервера должен быть доступ к этому пути.  
  
```csharp  
using (SqlConnection connection = New SqlConnection(connectionString))  
{  
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +  
    "FROM 'f:\mydata\data.tbl' " +  
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";  
connection.Open();  
SqlCommand command = new SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery();  
}  
```  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Операции массового копирования в SQL Server](bulk-copy-operations-sql-server.md)
