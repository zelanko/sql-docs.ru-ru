---
title: SQLSTATE (коды ошибок ODBC) | Документация Майкрософт
description: Когда SQL Server драйвер ODBC запускает хранимые процедуры в качестве удаленных хранимых процедур, процедура может иметь целочисленные коды возврата и выходные параметры.
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a1547fc47aaca643852b5f381567d64ecc3b3f06
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967649"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (коды ошибок ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Код SQLSTATE предоставляет подробные сведения о причине предупреждения или ошибки. Для ошибок, возникающих в источнике данных, обнаруженном и возвращенном [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента сопоставляет возвращенный номер собственной ошибки с соответствующим SQLSTATE. Если машинный номер ошибки не имеет кода ошибки ODBC для сопоставлений, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента возвращает значение SQLSTATE 42000 ("Синтаксическая ошибка или нарушение прав доступа"). Для ошибок, обнаруженных драйвером, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента создает соответствующее значение SQLSTATE.  
  
 Дополнительные сведения о кодах ошибок состояния см. в следующих разделах.  
  
-   [Приложение А. Коды ошибок ODBC](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [Сопоставления SQLSTATE](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>См. также:  
 [Обработка ошибок и сообщений](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
