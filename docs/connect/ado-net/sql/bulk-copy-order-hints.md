---
title: Указания порядка для операций массового копирования
description: Описывает, как использовать указания порядка в операциях массового копирования.
ms.date: 06/15/2020
dev_langs:
- csharp
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: johnnypham
ms.author: v-jopha
ms.reviewer: ''
ms.openlocfilehash: c7365bdc6da75e04d019ca1a6a87b90dd8d4ec3c
ms.sourcegitcommit: 6b3569977b034554883a94d73d1c4df6e2f74fe2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2020
ms.locfileid: "85110185"
---
# <a name="order-hints-for-bulk-copy-operations"></a>Указания порядка для операций массового копирования

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Операции массового копирования обеспечивают значительный выигрыш в производительности по сравнению с другими методами загрузки данных в таблицу SQL Server. Производительность можно дополнительно улучшить с помощью указаний порядка. Указания порядка для операций массового копирования сокращают время вставки отсортированных данных в таблицы с кластеризованными индексами.

По умолчанию операция массовой вставки считает, что входящие данные не упорядочены. SQL Server принудительно выполняет промежуточную сортировку этих данных перед их массовый загрузкой. Если вы уверены, что ваши входящие данные уже отсортированы, можно использовать указания порядка, чтобы сообщить операции массового копирования о порядке сортировки всех целевых столбцов, которые являются частью кластеризованного индекса.
  
## <a name="adding-order-hints-to-a-bulk-copy-operation"></a>Добавление указаний порядка в операцию массового копирования  
В следующем примере выполняется массовое копирование данных из исходной таблицы в примере базы данных **AdventureWorks** в целевую таблицу в той же базе данных. Создается объект SqlBulkCopyColumnOrderHint для определения порядка сортировки столбца **ProductNumber** в целевой таблице. Указание порядка добавляется в экземпляр SqlBulkCopy, который добавляет соответствующий аргумент указания порядка к результирующему запросу `INSERT BULK`.

[!code-csharp [SqlBulkCopy.ColumnOrderHint#1](~/../sqlclient/doc/samples/SqlBulkCopy_ColumnOrderHint.cs#1)]

## <a name="next-steps"></a>Дальнейшие действия
- [Операции массового копирования в SQL Server](bulk-copy-operations-sql-server.md)
