---
title: SQL Server результаты сообщения | Документация Майкрософт
description: результаты сообщения SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 05d731f418bad21f9e8ec32c620b352c5663994a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994920"
---
# <a name="sql-server-message-results"></a>Результаты сообщения SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Следующие инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] не создают при работе наборы строк поставщика драйвера OLE DB для SQL Server и не возвращают количество обработанных строк:  
  
-   PRINT  
  
-   RAISERROR (со степенью серьезности 10 или ниже)  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Эти инструкции либо возвращают одно или несколько информационных сообщений, либо дают указание [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] вернуть информационные сообщения вместо набора строк или результатов вычислений. При успешном выполнении Драйвер OLE DB для SQL Server возвращает значение S_OK, и сообщения становятся доступными драйверу OLE DB для SQL Server потребителя.  
  
 Драйвер OLE DB для SQL Server возвращает значение S_OK и содержит одно или несколько информационных сообщений, доступных после выполнения множества [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкций или выполнения пользователем драйвера OLE DB для SQL Server функции-члена.  
  
 Потребитель драйвера OLE DB для SQL Server, разрешающий динамическую спецификацию текста запроса, должен проверять интерфейсы ошибок после каждого выполнения функции-члена независимо от значения кода возврата, наличия или отсутствия возвращенной ссылки на интерфейс **IRowset** или **IMultipleResults** или количества обработанных строк.  
  
## <a name="see-also"></a>См. также:  
 [ошибки](../../oledb/ole-db-errors/errors.md)  
  
  
