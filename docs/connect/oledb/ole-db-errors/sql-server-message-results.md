---
title: Результаты сообщения SQL Server | Документация Майкрософт
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
ms.openlocfilehash: dfebd7443b24d09e6bf7696caba5449c1890e0d2
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "85998288"
---
# <a name="sql-server-message-results"></a>Результаты сообщения SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Следующие инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] не создают при работе наборы строк поставщика драйвера OLE DB для SQL Server и не возвращают количество обработанных строк:  
  
-   PRINT  
  
-   RAISERROR (со степенью серьезности 10 или ниже)  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Эти инструкции либо возвращают одно или несколько информационных сообщений, либо дают указание [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] вернуть информационные сообщения вместо набора строк или результатов вычислений. При успешном выполнении OLE DB Driver for SQL Server возвращает значение S_OK, а сообщения становятся доступны потребителю OLE DB Driver for SQL Server.  
  
 OLE DB Driver for SQL Server возвращает значение S_OK и предоставляет одно или несколько информационных сообщений после выполнения многих инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)] или при выполнении потребителем функции-члена OLE DB Driver for SQL Server.  
  
 Потребитель драйвера OLE DB для SQL Server, разрешающий динамическую спецификацию текста запроса, должен проверять интерфейсы ошибок после каждого выполнения функции-члена независимо от значения кода возврата, наличия или отсутствия возвращенной ссылки на интерфейс **IRowset** или **IMultipleResults** или количества обработанных строк.  
  
## <a name="see-also"></a>См. также:  
 [ошибки](../../oledb/ole-db-errors/errors.md)  
  
  
