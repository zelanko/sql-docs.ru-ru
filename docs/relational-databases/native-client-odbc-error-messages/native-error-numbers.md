---
title: Собственные номера ошибок | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, native error numbers
- SQL Server Native Client ODBC driver, errors
- native error numbers [SQL Server Native Client]
- messages [ODBC], native error numbers
- errors [ODBC], native error numbers
ms.assetid: 77cbc826-f47f-4803-8e7a-223d6df069b1
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c1a66e011ee5716f92d8b0257ed8424c86244139
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62738732"
---
# <a name="native-error-numbers"></a>Собственные коды ошибок
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Для ошибок, возникающих в источнике данных (возвращенный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента возвращает номер собственной ошибки, переданные ему из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для ошибок, обнаруженных драйвером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента возвращает собственный код ошибки 0. Дополнительные сведения о списке собственных кодов ошибок см. в столбце error **sysmessages** системная таблица в **master** базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Сведения о кодах ошибок состояния см. в разделе [SQLSTATE &#40;коды ошибок ODBC&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md). В случае ошибок, возвращаемых библиотекой Net-Library, собственный код ошибки можно получить из базового сетевого программного обеспечения.  
  
## <a name="see-also"></a>См. также  
 [Обработка ошибок и сообщений](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
