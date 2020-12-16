---
title: Реализация IDENTITY в оптимизированной для памяти таблице | Документация Майкрософт
description: Узнайте об IDENTITY в таблицах, оптимизированных для памяти, в SQL Server. Оптимизированные для памяти таблицы поддерживают IDENTITY для начального и инкрементного значений.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ef0fb83f092d2920ab36bf977edd18a6dda71e28
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97460447"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>Реализация IDENTITY в таблице, оптимизированной для памяти
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

IDENTITY поддерживается в оптимизированной для памяти таблице, если и начальное значение, и шаг приращения равны 1 (по умолчанию). Столбцы идентификаторов с определением IDENTITY(x, y), где x != 1 или y != 1 в таблицах, оптимизированных для памяти, не поддерживаются.   
    
Чтобы увеличить начальное значение IDENTITY, вставьте новую строку с явным значением в столбце идентификаторов с помощью параметра сеанса `SET IDENTITY_INSERT table_name ON`. При вставке строки начальное значение IDENTITY меняется на явно добавленное значение плюс 1. Например, чтобы увеличить начальное значение до 1000, вставьте строку со значением 999 в столбце идентификаторов. Создаваемые значения идентификаторов будут начинаться с 1000.     
  
## <a name="see-also"></a>См. также:  
 [Миграция в In-Memory OLTP](./plan-your-adoption-of-in-memory-oltp-features-in-sql-server.md)  
  
