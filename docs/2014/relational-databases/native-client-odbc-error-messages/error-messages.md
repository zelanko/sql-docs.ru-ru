---
title: Сообщения об ошибках | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bbf73940b92ef158e4e93b10c2142c9053703f5f
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705407"
---
# <a name="error-messages"></a>сообщения об ошибках
  Текст сообщений, возвращаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвером ODBC для собственного клиента, помещается в параметр *MessageText* объекта **SQLGetDiagRec**. На источник ошибки указывает заголовок сообщения.  
  
 [Майкрософт][Диспетчер драйверов ODBC]  
 Эти ошибки формируются диспетчером драйверов ODBC.  
  
 [Майкрософт][Библиотека курсоров ODBC]  
 Эти ошибки формируются библиотекой курсоров ODBC.  
  
 [Майкрософт][Собственный клиент SQL Server]  
 Эти ошибки вызываются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвером ODBC для собственного клиента. Если не существует других узлов с именем сетевой библиотеки или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то ошибка произошла в драйвере.  
  
 NNTP [SQL Server Native Client] [*Net-транспорта*]  
 Эти ошибки вызываются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сетевой библиотекой, где *net-транспорта* — отображаемое имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сетевого транспорта клиента (например, именованные каналы, Общая память, сокеты TCP/IP или Via). Остальная часть сообщения об ошибке содержит вызванную функцию сетевой библиотеки и функцию, вызванную в базовом сетевом API-интерфейсе функцией потока табличных данных. Код ошибки *pfNative* , возвращенный с этими ошибками, является кодом ошибки из базового стека сетевых протоколов.  
  
 [Майкрософт] [Собственный клиент SQL Server][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 Эти ошибки формируются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Остальная часть сообщения об ошибке — текст сообщения об ошибке из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Код *pfNative* , возвращенный с этими ошибками, является номером ошибки из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения о списке сообщений об ошибках (и их номерах), которые могут быть возвращены [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. в столбцах Description и Error системной таблицы **sysmessages** в базе данных **master** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Обработка ошибок и сообщений](handling-errors-and-messages.md)  
  
  
