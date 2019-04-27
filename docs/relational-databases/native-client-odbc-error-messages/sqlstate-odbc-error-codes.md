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
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 18f7ebab7d6463c419d31464c1343d6fd03d4cec
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62738836"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (коды ошибок ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Код SQLSTATE предоставляет подробные сведения о причине предупреждения или ошибки. Для ошибок, возникающих в данных источника, выявляются и возвращаются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента сопоставляет возвращенный собственный номер ошибки с соответствующим кодом SQLSTATE. Если собственный номер ошибки не является кодом ошибки ODBC, которое будет сопоставлено, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента возвращает сообщение SQLSTATE 42000 («синтаксическая ошибка или нарушение доступа»). Для ошибки, обнаруженные с помощью драйвера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента создает соответствующий код SQLSTATE.  
  
 Дополнительные сведения о кодах ошибок состояния см. в следующих разделах.  
  
-   [Приложение а. Коды ошибок ODBC](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [Сопоставления SQLSTATE](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>См. также  
 [Обработка ошибок и сообщений](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
