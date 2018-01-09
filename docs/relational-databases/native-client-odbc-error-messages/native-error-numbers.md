---
title: "Номера собственных ошибок | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-error-messages
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, native error numbers
- SQL Server Native Client ODBC driver, errors
- native error numbers [SQL Server Native Client]
- messages [ODBC], native error numbers
- errors [ODBC], native error numbers
ms.assetid: 77cbc826-f47f-4803-8e7a-223d6df069b1
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 49fbc1ffedf678170bf08306220a7389cf1ed3f4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="native-error-numbers"></a>Собственные коды ошибок
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Для ошибок, возникающих в источнике данных (возвращенный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента возвращает номер собственной ошибки, переданные ему из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для ошибок, обнаруженных драйвером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента возвращает номер собственной ошибки 0. Дополнительные сведения о списке собственных кодов ошибок см. в столбце error **sysmessages** системная таблица в **master** базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Сведения о кодах ошибок состояния см. в разделе [SQLSTATE &#40; коды ошибок ODBC &#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md). В случае ошибок, возвращаемых библиотекой Net-Library, собственный код ошибки можно получить из базового сетевого программного обеспечения.  
  
## <a name="see-also"></a>См. также:  
 [Обработка ошибок и сообщений](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
