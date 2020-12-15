---
description: Выборка строк — следующая выборка (поставщик собственного клиента OLE DB)
title: Следующее расположение выборки (поставщик собственного клиента OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 819d790e94026be70861e1fe3d1d4ad547ca77e9
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97483155"
---
# <a name="fetching-rows---next-fetch--native-client-ole-db-provider"></a>Выборка строк — следующая выборка (поставщик собственного клиента OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента отслеживает положение следующей выборки таким образом, что последовательность вызовов метода **GetNextRows** (без пропуска, изменения направления или промежуточных вызовов методов **FindNextRow**, **Seek** или **свойство RestartPosition** ) считывает весь набор строк без пропуска или повторения какой-либо строки. Позиция следующей выборки меняется с помощью вызова методов **IRowset::GetNextRows**, **IRowset::RestartPosition** или **IRowsetIndex::Seek** либо вызовом **FindNextRow** со значением *pBookmark*, равным NULL. Вызов **FindNextRow** со значением *pBookmark*, отличным от NULL, не влияет на позицию следующей выборки.  
  
## <a name="see-also"></a>См. также:  
 [Выборка строк](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
  
