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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b9612fbd7dd50ffeec812532e25a63eecca26571
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705366"
---
# <a name="native-error-numbers"></a>Собственные коды ошибок
  Для ошибок, возникающих в источнике данных (возвращенном [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента возвращает номер собственной ошибки, возвращенный ей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для ошибок, обнаруженных драйвером, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента возвращает номер собственной ошибки, равный 0. Дополнительные сведения о списке машинных номеров ошибок см. в столбце "ошибка" системной таблицы **sysmessages** в базе данных **master** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Сведения о кодах ошибок состояния см. в разделе [SQLSTATE &#40;коды ошибок ODBC&#41;](sqlstate-odbc-error-codes.md). В случае ошибок, возвращаемых библиотекой Net-Library, собственный код ошибки можно получить из базового сетевого программного обеспечения.  
  
## <a name="see-also"></a>См. также  
 [Обработка ошибок и сообщений](handling-errors-and-messages.md)  
  
  
