---
title: Собственные номера ошибок | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 7e7cd24a3eb1ccdeea1b6e6cbb97e2d0f222193f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48180284"
---
# <a name="native-error-numbers"></a>Собственные коды ошибок
  Для ошибок, возникающих в источнике данных (возвращенный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента возвращает номер собственной ошибки, переданные ему из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для ошибок, обнаруженных драйвером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента возвращает собственный код ошибки 0. Дополнительные сведения о списке собственных кодов ошибок см. в столбце error **sysmessages** системная таблица в **master** базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Сведения о кодах ошибок состояния см. в разделе [SQLSTATE &#40;коды ошибок ODBC&#41;](sqlstate-odbc-error-codes.md). В случае ошибок, возвращаемых библиотекой Net-Library, собственный код ошибки можно получить из базового сетевого программного обеспечения.  
  
## <a name="see-also"></a>См. также  
 [Обработка ошибок и сообщений](handling-errors-and-messages.md)  
  
  
