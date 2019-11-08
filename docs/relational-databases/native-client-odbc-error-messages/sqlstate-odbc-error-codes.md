---
title: SQLSTATE (коды ошибок ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- ODBC error handling, cause information
- messages [ODBC], cause information
- SQLSTATEs
- errors [ODBC], cause information
ms.assetid: 84cce528-edb0-473f-a85f-3eb87fbe2cf3
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 162f6ff15a95c1839ef59b10c659935b687aeb59
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73783210"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (коды ошибок ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Код SQLSTATE предоставляет подробные сведения о причине предупреждения или ошибки. Для ошибок, возникающих в источнике данных, обнаруженном и возвращаемом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сопоставляет возвращенный номер собственной ошибки с соответствующим SQLSTATE. Если номер собственной ошибки не содержит код ошибки ODBC для сопоставлений, драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение SQLSTATE 42000 ("Синтаксическая ошибка или нарушение прав доступа"). Для ошибок, обнаруженных драйвером, драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает соответствующее значение SQLSTATE.  
  
 Дополнительные сведения о кодах ошибок состояния см. в следующих разделах.  
  
-   [Приложение А. Коды ошибок ODBC](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [Сопоставления SQLSTATE](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>См. также раздел  
 [Обработка ошибок и сообщений](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
