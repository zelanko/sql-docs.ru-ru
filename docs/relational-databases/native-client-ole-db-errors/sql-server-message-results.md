---
title: SQL Server результаты сообщения | Документация Майкрософт
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3383dcd08ed5910d949608e521b3cd23f37aace8
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73790150"
---
# <a name="sql-server-message-results"></a>Результаты сообщения SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] не создают [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственные наборы строк поставщика OLE DB клиента или количество затронутых строк при выполнении:  
  
-   PRINT  
  
-   RAISERROR (со степенью серьезности 10 или ниже)  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Эти инструкции либо возвращают одно или несколько информационных сообщений, либо дают указание [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вернуть информационные сообщения вместо набора строк или результатов вычислений. При успешном выполнении поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB возвращает S_OK, а сообщения становятся доступными для клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB поставщика.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает S_OK и имеет одно или несколько информационных сообщений, доступных после выполнения многих инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или выполнения пользовательской функции-члена [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика собственного клиента OLE DB Native Client.  
  
 Потребитель поставщика OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который разрешает динамической спецификации текста запроса, должен проверять интерфейсы ошибок после каждого выполнения функции-члена независимо от значения кода возврата, наличия или отсутствия возвращенной программы **IRowset** или ссылка на интерфейс **IMultipleResults** или количество затронутых строк.  
  
## <a name="see-also"></a>См. также раздел  
 [ошибки](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
