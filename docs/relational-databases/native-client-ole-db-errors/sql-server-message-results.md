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
ms.openlocfilehash: 577b609fd2f878e6c97010cac004e0b10b3a4e4e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300984"
---
# <a name="sql-server-message-results"></a>Результаты сообщения SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Следующие [!INCLUDE[tsql](../../includes/tsql-md.md)] операторы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не генерируют строки поставщика Native Client OLE DB или подсчет затронутых строк при выполнении:  
  
-   PRINT  
  
-   RAISERROR (со степенью серьезности 10 или ниже)  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Эти инструкции либо возвращают одно или несколько информационных сообщений, либо дают указание [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вернуть информационные сообщения вместо набора строк или результатов вычислений. При успешном [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] исполнении поставщик Native Client OLE DB возвращает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] S_OK, а сообщения доступны потребителю-поставщику NATIVE Client OLE DB.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает S_OK и имеет одно или [!INCLUDE[tsql](../../includes/tsql-md.md)] несколько информационных сообщений, доступных после выполнения многих инструкций или исполнения потребителями функции поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] услуг Native Client OLE DB.  
  
 Потребитель-поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB, позволяющий динамическую спецификацию текста запроса, должен проверять интерфейсы ошибок после выполнения каждой функции участника, независимо от значения кода возврата, наличия или отсутствия возвращенной ссылки на интерфейс **IRowset** или **IMultipleResults** или подсчета затронутых строк.  
  
## <a name="see-also"></a>См. также:  
 [ошибки](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
