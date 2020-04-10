---
title: несколько операций массового копирования;
description: Узнайте, как выполнить нескольких операций массового копирования данных в экземпляр SQL Server с помощью класса SqlBulkCopy.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: a0a1f24970801698eedc8971f0db54bd08589945
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924297"
---
# <a name="multiple-bulk-copy-operations"></a>несколько операций массового копирования;

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Вы можете выполнить несколько операций массового копирования, используя один экземпляр класса <xref:Microsoft.Data.SqlClient.SqlBulkCopy>. Если между копированиями параметры операции изменяются (например, имя целевой таблицы), необходимо обновить их до последующих вызовов любого из методов **WriteToServer**, как показано в следующем примере. Если значения свойств не изменяются явным образом, все они остаются такими же, как при предыдущей операции массового копирования для данного экземпляра.  
  
> [!NOTE]
>  Выполнение нескольких операций массового копирования с использованием одного экземпляра <xref:Microsoft.Data.SqlClient.SqlBulkCopy> обычно более эффективно, чем использование отдельного экземпляра для каждой операции.  
  
При выполнении нескольких операций массового копирования с одним объектом <xref:Microsoft.Data.SqlClient.SqlBulkCopy> не существует ограничений, касающихся совпадения или различий целевой информации в каждой операции. Однако для каждой записи на сервер необходимо убедиться, что связи столбцов настроены правильно.  

## <a name="example"></a>Пример

> [!IMPORTANT]
>  Этот пример не будет работать, если вы не создали рабочие таблицы, как описано в разделе [Пример настройки массового копирования](bulk-copy-example-setup.md). Этот код предназначен только для демонстрации синтаксиса использования **SqlBulkCopy**. Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL `INSERT … SELECT` для копирования данных.  
  
[!code-csharp[DataWorks SqlBulkCopy_._ColumnMappingOrdersDetails#1](~/../sqlclient/doc/samples/SqlBulkCopy_ColumnMappingOrdersDetails.cs#1)]
  
## <a name="next-steps"></a>Дальнейшие действия
- [Операции массового копирования в SQL Server](bulk-copy-operations-sql-server.md)
