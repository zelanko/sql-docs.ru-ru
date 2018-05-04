---
title: Удаление таблицы SQL Server | Документы Microsoft
description: Удаление таблицы SQL Server с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- deleting tables
- OLE DB Driver for SQL Server, tables
- removing tables
- dropping tables
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 4efcf4e94ad5af62cb728980b7b139cf3bbf7ea4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="dropping-a-sql-server-table"></a>Удаление таблицы SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server предоставляет **ITableDefinition::DropTable** функцию удаления [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицы из базы данных.  
  
 Укажите имя таблицы в качестве строки символов в Юникоде в *pwszName* членом *uName* объединения в *pTableID* параметра. *EKind* членом *pTableID* должен быть равен DBKIND_NAME.  
  
## <a name="see-also"></a>См. также:  
 [Таблицы и индексы](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
