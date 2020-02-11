---
title: 'Использование IRow:: DataColumn | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 50608f4bb72f982ca5e4651ab5da3cb17cd35cf9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73761670"
---
# <a name="using-irowgetcolumns"></a>Использование метода IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Реализация интерфейса **IRow** позволяет перемещаться только вперед с последовательным доступом к столбцам. Столбцы этой строки можно получить либо полностью одним вызовом метода **IRow::GetColumns**, либо по частям, несколько раз вызывая метод **IRow::GetColumns** при доступе к нескольким столбцам строки.  
  
 Если метод **IRow::GetColumns** вызывается несколько раз, эти вызовы не должны перекрываться. Например, если первый вызов метода **IRow::GetColumns** возвращает столбцы 1, 2 и 3, то второй вызов **IRow::GetColumns** будет возвращать столбцы 4, 5 и 6. Если последующие вызовы **IRow::GetColumns** пересекаются, то флажку состояния (полю dwstatus в DBCOLUMNACCESS) присваивается значение DBSTATUS_E_UNAVAILABLE.  
  
## <a name="see-also"></a>См. также:  
 [Выборка одной строки при помощи интерфейса IRow](../../relational-databases/native-client-ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
