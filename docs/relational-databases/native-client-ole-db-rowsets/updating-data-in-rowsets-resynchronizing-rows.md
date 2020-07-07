---
title: Повторная синхронизация строк | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
ms.assetid: d2d30505-a878-4aa9-b821-53d8118a45a5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bf5a7bf6a7a35fd33fdbefe9ffc24b0ee3a7a9f3
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86013107"
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>Обновление данных в наборах строк — повторная синхронизация строк
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента поддерживает **интерфейс irowsetresynch** только для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наборов строк, поддерживаемых курсорами. Интерфейс **IRowsetResynch** не предоставляется по требованию. Пользователь должен запросить этот интерфейс перед открытием набора строк.  
  
## <a name="see-also"></a>См. также  
 [Обновление данных в наборах строк](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
