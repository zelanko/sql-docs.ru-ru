---
title: Номера покоренных ошибок (ru) Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0b5572ee784f47b0444e1d825de1b6dd53db8066
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291614"
---
# <a name="native-error-numbers"></a>Собственные коды ошибок
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Для ошибок, которые происходят [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источнике данных (возвращается), водитель Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Client ODBC возвращает исходный номер ошибки, возвращенный ему. Для ошибок, обнаруженных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] водителем, водитель Native Client ODBC возвращает номер ошибки 0. Для получения дополнительной информации о списке родных **sysmessages** номеров ошибок, см. **master** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Для получения информации о кодах ошибок состояния, см [&#41;&#40;. ](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md) В случае ошибок, возвращаемых библиотекой Net-Library, собственный код ошибки можно получить из базового сетевого программного обеспечения.  
  
## <a name="see-also"></a>См. также:  
 [Обработка ошибок и сообщений](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
