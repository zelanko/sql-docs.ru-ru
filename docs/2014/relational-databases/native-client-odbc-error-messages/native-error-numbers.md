---
title: Номера собственных ошибок | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, native error numbers
- SQL Server Native Client ODBC driver, errors
- native error numbers [SQL Server Native Client]
- messages [ODBC], native error numbers
- errors [ODBC], native error numbers
ms.assetid: 77cbc826-f47f-4803-8e7a-223d6df069b1
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: faee9067ccf8f60a4b7dade849a0a987b5c07bd0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187753"
---
# <a name="native-error-numbers"></a>Собственные коды ошибок
  Для ошибок, возникающих в источнике данных (возвращенный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента возвращает номер собственной ошибки, переданные ему из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для ошибок, обнаруженных драйвером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента возвращает номер собственной ошибки 0. Дополнительные сведения о списке собственных кодов ошибок см. в столбце error **sysmessages** системная таблица в **master** базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Сведения о кодах ошибок состояния см. в разделе [SQLSTATE &#40;коды ошибок ODBC&#41;](sqlstate-odbc-error-codes.md). В случае ошибок, возвращаемых библиотекой Net-Library, собственный код ошибки можно получить из базового сетевого программного обеспечения.  
  
## <a name="see-also"></a>См. также  
 [Обработка ошибок и сообщений](handling-errors-and-messages.md)  
  
  