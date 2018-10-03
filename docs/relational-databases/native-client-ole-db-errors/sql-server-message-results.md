---
title: Результаты сообщения SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2d48f69fa3b5ca335f327a8aa2411f3973a2cdbe
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850942"
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
  
 Эти инструкции либо возвращают одно или несколько информационных сообщений, либо дают указание [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вернуть информационные сообщения вместо набора строк или результатов вычислений. При успешном выполнении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает S_OK, поставщик OLE DB для собственного клиента, и сообщения доступны для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителем поставщика OLE DB для собственного клиента.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента, возвращается значение s_ок и имеет один или несколько информационных сообщений, появляющихся после выполнения многих [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций или при выполнении потребителем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] член поставщика OLE DB для собственного клиента функция.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Потребителем поставщика OLE DB для собственного клиента, разрешающий динамическую спецификацию текста запроса должен проверять интерфейсы ошибок после каждого члена функции выполнения независимо от значения кода возврата, наличия или отсутствия возвращаемого **IRowset** или **IMultipleResults** Справочник по интерфейсу, или количество затронутых строк.  
  
## <a name="see-also"></a>См. также  
 [ошибки](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
