---
title: Реализация IDENTITY в оптимизированной для памяти таблице | Документация Майкрософт
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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 670cbaf1532c5d958c746ec8645a02815a7e5c01
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47631362"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>Реализация IDENTITY в таблице, оптимизированной для памяти
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

IDENTITY поддерживается в оптимизированной для памяти таблице, если и начальное значение, и шаг приращения равны 1 (по умолчанию). Столбцы идентификаторов с определением IDENTITY(x, y), где x != 1 или y != 1 в таблицах, оптимизированных для памяти, не поддерживаются.   
    
Чтобы увеличить начальное значение IDENTITY, вставьте новую строку с явным значением в столбце идентификаторов с помощью параметра сеанса `SET IDENTITY_INSERT table_name ON`. При вставке строки начальное значение IDENTITY меняется на явно добавленное значение плюс 1. Например, чтобы увеличить начальное значение до 1000, вставьте строку со значением 999 в столбце идентификаторов. Создаваемые значения идентификаторов будут начинаться с 1000.     
  
## <a name="see-also"></a>См. также:  
 [Миграция в In-Memory OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
