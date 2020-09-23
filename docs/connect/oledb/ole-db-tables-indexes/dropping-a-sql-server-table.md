---
title: Удаление таблицы SQL Server (драйвер OLE DB) | Документация Майкрософт
description: Узнайте, как удалить таблицу SQL Server из базы данных с помощью функции ITableDefinition::DropTable в OLE DB Driver for SQL Server.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- deleting tables
- OLE DB Driver for SQL Server, tables
- removing tables
- dropping tables
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c3bdcc2b2b96c2cd1d9af0bbf7d31457eed71381
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88859400"
---
# <a name="dropping-a-sql-server-table"></a>Удаление таблицы SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В драйвере OLE DB для SQL Server доступна функция **ITableDefinition::DropTable**, которая позволяет удалять из базы данных таблицу [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Задайте имя таблицы в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pTableID*. Элемент *eKind* параметра *pTableID* должен быть равен DBKIND_NAME.  
  
## <a name="see-also"></a>См. также:  
 [Таблицы и индексы](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
