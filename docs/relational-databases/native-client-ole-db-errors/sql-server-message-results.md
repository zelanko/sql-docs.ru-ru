---
title: "Результаты сообщения SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-errors
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f5a8aa363b7a60da6dbc67fdf6cdc7ef8059ec88
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="sql-server-message-results"></a>Результаты сообщения SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Следующие [!INCLUDE[tsql](../../includes/tsql-md.md)] операторы не приводят к формированию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наборы строк поставщика OLE DB для собственного клиента или количество обработанных строк:  
  
-   PRINT  
  
-   RAISERROR (со степенью серьезности 10 или ниже)  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Эти инструкции либо возвращают одно или несколько информационных сообщений, либо дают указание [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вернуть информационные сообщения вместо набора строк или результатов вычислений. При успешном выполнении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента возвращает значение S_OK, и сообщения доступны для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителем поставщика OLE DB для собственного клиента.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает значение S_OK и имеет один или несколько информационных сообщений, появляющихся после выполнения многих [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции или выполнении потребителем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функция-член поставщика OLE DB для собственного клиента.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Потребителем поставщика OLE DB для собственного клиента, разрешающий динамическую спецификацию текста запроса должен проверять интерфейсы ошибок после каждого члена функции выполнения независимо от значения кода возврата, наличия или отсутствия возвращенной **IRowset** или **IMultipleResults** Справочник по интерфейсу или количество затронутых строк.  
  
## <a name="see-also"></a>См. также:  
 [ошибки](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
