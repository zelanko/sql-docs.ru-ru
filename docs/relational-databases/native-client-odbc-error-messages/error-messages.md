---
title: Сообщения об ошибках (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7d632d1d22cd8439a3d787e22301ec06ec4e0d93
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291794"
---
# <a name="error-messages"></a>сообщения об ошибках
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Текст сообщений, возвращенных драйвером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC, размещен в параметре *MessageText* компании **S'LGetDiagRec**. На источник ошибки указывает заголовок сообщения.  
  
 [Майкрософт][Диспетчер драйверов ODBC]  
 Эти ошибки формируются диспетчером драйверов ODBC.  
  
 [Майкрософт][Библиотека курсоров ODBC]  
 Эти ошибки формируются библиотекой курсоров ODBC.  
  
 [Майкрософт][Собственный клиент SQL Server]  
 Эти ошибки поднимаются драйвером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC. Если не существует других узлов с именем сетевой библиотеки или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то ошибка произошла в драйвере.  
  
 (Microsoft) «Родной клиент сервера» *Чистая транспортная фамилия*  
 Эти ошибки поднимаются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Net-Library, где *Net-Transportname* — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это отображение клиентского сетевого транспорта (например, Named Pipes, Shared Memory, TCP/IP Sockets или VIA). Остальная часть сообщения об ошибке содержит вызванную функцию сетевой библиотеки и функцию, вызванную в базовом сетевом API-интерфейсе функцией потока табличных данных. Код ошибки *pfNative,* возвращенный с помощью этих ошибок, является кодом ошибки из базового стека сетевого протокола.  
  
 (Microsoft) «Родной клиент сервера» [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 Эти ошибки формируются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Остальная часть сообщения об ошибке — текст сообщения об ошибке из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *PfNative* код вернулся с этими [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ошибками является номер ошибки от . Для получения дополнительной информации о списке сообщений об [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ошибках (и их номера), **sysmessages** которые могут быть возвращены, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]см. **master**  
  
## <a name="see-also"></a>См. также:  
 [Обработка ошибок и сообщений](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
