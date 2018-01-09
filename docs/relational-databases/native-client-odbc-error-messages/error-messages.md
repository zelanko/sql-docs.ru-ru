---
title: "Сообщения об ошибках | Документы Microsoft"
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
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9eaa5f64629ce0d1b5fb9523466278fc767d50e4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="error-messages"></a>сообщения об ошибках
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Текст сообщения, возвращаемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента помещается в *MessageText* параметр **SQLGetDiagRec**. На источник ошибки указывает заголовок сообщения.  
  
 [Майкрософт][Диспетчер драйверов ODBC]  
 Эти ошибки формируются диспетчером драйверов ODBC.  
  
 [Майкрософт][Библиотека курсоров ODBC]  
 Эти ошибки формируются библиотекой курсоров ODBC.  
  
 [Майкрософт][Собственный клиент SQL Server]  
 Эти ошибки формируются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента. Если не существует других узлов с именем сетевой библиотеки или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то ошибка произошла в драйвере.  
  
 [Microsoft] [Собственный клиент SQL Server] [*Сетевого транспорта*]  
 Эти ошибки формируются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Net-Library, где *сетевого транспорта* отображаемое имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] клиентского сетевого транспорта (например, именованные каналы, общая память, сокеты TCP/IP или VIA). Остальная часть сообщения об ошибке содержит вызванную функцию сетевой библиотеки и функцию, вызванную в базовом сетевом API-интерфейсе функцией потока табличных данных. *PfNative* код ошибки, возвращенный с этими ошибками — код ошибки из базового сетевого стека протокола.  
  
 [Майкрософт] [Собственный клиент SQL Server][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 Эти ошибки формируются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Остальная часть сообщения об ошибке — текст сообщения об ошибке из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *PfNative* код, возвращенный с этими ошибками — номер ошибки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения о списке сообщений об ошибках (и их номерах) может быть возвращен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], description и error столбцов **sysmessages** системная таблица в **master** База данных, в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Обработка ошибок и сообщений](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
