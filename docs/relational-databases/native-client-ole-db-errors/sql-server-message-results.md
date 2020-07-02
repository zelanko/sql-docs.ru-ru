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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9d45654e204be862ed335d688d16294526892054
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773395"
---
# <a name="sql-server-message-results"></a>Результаты сообщения SQL Server
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Следующие [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции не создают [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственные наборы строк поставщика OLE DB клиента или число затронутых строк при выполнении:  
  
-   PRINT  
  
-   RAISERROR (со степенью серьезности 10 или ниже)  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Эти инструкции либо возвращают одно или несколько информационных сообщений, либо дают указание [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вернуть информационные сообщения вместо набора строк или результатов вычислений. При успешном выполнении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB возвращает S_OK, и сообщения становятся доступными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителю поставщика собственного клиента OLE DB.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента возвращает S_OK и имеет одно или несколько информационных сообщений, доступных после выполнения множества [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций или выполнения пользовательской [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функции-члена поставщика собственного клиента OLE DB.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Потребитель поставщика OLE DB собственного клиента, который разрешает динамической спецификации текста запроса, должен проверять интерфейсы ошибок после каждого выполнения функции-члена независимо от значения кода возврата, наличия или отсутствия возвращенной ссылки на интерфейс **IRowset** или **IMultipleResults** или количества затронутых строк.  
  
## <a name="see-also"></a>См. также:  
 [ошибки](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
