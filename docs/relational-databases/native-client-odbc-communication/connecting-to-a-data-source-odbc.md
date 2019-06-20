---
title: Подключение к источнику данных (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- checking connection states
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- SQLBrowseConnect function
- ODBC applications, connections
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLConnect function
- SQLDriveConnect function
- verifying connection states
- SQL Server Native Client ODBC driver, data sources
- SQL Server Native Client ODBC driver, connections
ms.assetid: ae30dd1d-06ae-452b-9618-8fd8cd7ba074
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a6ebe847e999d83343b072938882b9fd9e51b290
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63013961"
---
# <a name="connecting-to-a-data-source-odbc"></a>Соединение с источником данных (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  После определения среды и дескрипторов соединения, а также установки любых атрибутов соединения приложение устанавливает соединение с источником данных или драйвером. Существует три функции, которые можно использовать для установки соединения:  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLBrowseConnect**  
  
 Дополнительные сведения о подключении к источнику данных, включая различные доступные параметры строки соединения, см. в разделе [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
## <a name="sqlconnect"></a>SQLConnect  
 **SQLConnect** является простейшей функцией соединения. Она принимает три параметра: имя источника данных, идентификатор пользователя и пароль. Используйте **SQLConnect** когда следующие три параметра содержат всю информацию, необходимую для подключения к базе данных. Для этого построения списка источников данных с помощью **SQLDataSources**; запрашивать пользователя для источника данных, идентификатор пользователя и пароль; и затем вызвать **SQLConnect**.  
  
 **SQLConnect** предполагается, что имя источника данных, идентификатор пользователя и пароль достаточны для подключения к источнику данных и что источник данных ODBC содержит все сведения, которые необходимы драйверу ODBC для подключения. В отличие от [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) и [SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md), **SQLConnect** не использует строку подключения.  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
 **SQLDriverConnect** используется, когда требуется больше информации, чем имя источника данных, идентификатор пользователя и пароль. Один из параметров для **SQLDriverConnect** представляет собой строку соединения, содержащий сведения, относящиеся к драйверу. Можно использовать **SQLDriverConnect** вместо **SQLConnect** по следующим причинам:  
  
-   для указания специфической для драйвера информации во время подключения;  
  
-   для запроса, который драйвер направляет пользователю для получения информации о соединении;  
  
-   для соединения без использования источника данных ODBC.  
  
 **SQLDriverConnect** строка подключения содержит ряд пар "ключевое слово значение", укажите все сведения о соединении, поддерживаемые драйвером ODBC. Каждый драйвер поддерживает стандартные ключевые слова ODBC (DSN, FILEDSN, DRIVER, UID, PWD и SAVEFILE) в дополнение к специальным ключевым словам драйвера для указания всей информации о соединении, поддерживаемой драйвером. **SQLDriverConnect** может использоваться для подключения без источника данных. Например, приложения, разработанные для облегчения «Без DSN» подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно вызвать **SQLDriverConnect** со строкой соединения, который определяет идентификатор входа, пароль, сетевую библиотеку, имя сервера, чтобы Подключитесь к, и база данных для использования по умолчанию.  
  
 При использовании **SQLDriverConnect**, существует два варианта для подсказки пользователю необходимой для соединения информации:  
  
-   Диалоговое окно приложения  
  
     Можно создать диалоговое окно приложения, запросит информацию о соединении, а затем вызывает **SQLDriverConnect** с дескриптором окна NULL и *DriverCompletion* установлен в значение SQL_DRIVER_NOPROMPT. Эти параметры предотвращают открытие драйвером ODBC собственного диалогового окна. Этот метод используется, когда важно управлять пользовательским интерфейсом приложения.  
  
-   Диалоговое окно драйвера  
  
     Вы можете писать код приложения для передачи на допустимый дескриптор окна для **SQLDriverConnect** и задайте *DriverCompletion* SQL_DRIVER_COMPLETE, SQL_DRIVER_PROMPT или SQL_DRIVER_COMPLETE_ параметра Обязательно. Затем драйвер формирует диалоговое окно для получения от пользователя информации о соединении. Этот метод упрощает код приложения.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
 **SQLBrowseConnect**, например **SQLDriverConnect**, использует строку подключения. Тем не менее, с помощью **SQLBrowseConnect**, приложение может создать полную строку подключения взаимодействует с источником данных во время выполнения. Это позволяет приложению:  
  
-   строить собственные диалоговые окна для запроса этой информации, сохраняя таким образом управление своим пользовательским интерфейсом;  
  
-   просматривать систему в поисках источников данных, которые может использовать конкретный драйвер, возможно, за несколько шагов.  
  
     Например, пользователь может сначала просмотреть серверы в сети, а после выбора сервера с помощью драйвера просмотреть доступные базы данных этого сервера.  
  
 Когда **SQLBrowseConnect** завершения успешного подключения он возвращает строку подключения, который может использоваться при последующих вызовах **SQLDriverConnect**.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента всегда возвращает значение SQL_SUCCESS_WITH_INFO на удачный **SQLConnect**, **SQLDriverConnect**, или **SQLBrowseConnect**. Если приложение ODBC вызывает **SQLGetDiagRec** после получения SQL_SUCCESS_WITH_INFO, оно может получать следующие сообщения:  
  
 5701  
 Показывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] помещает пользовательский контекст в базу данных по умолчанию, которая определена в источнике данных, или в базу данных, определенную для идентификатора входа, который использовался в соединении, если источник данных не имеет базы данных по умолчанию.  
  
 5703  
 Обозначает язык, используемый на сервере.  
  
 В следующих примерах показано сообщение, которое возвращается системным администратором при успешном соединении:  
  
```  
szSqlState = "01000", *pfNativeError = 5701,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed database context to 'pubs'."  
szSqlState = "01000", *pfNativeError = 5703,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed language setting to 'us_english'."  
```  
  
 Можно не обрабатывать сообщения 5701 и 5703; они всего лишь информационные. Однако не следует пропускать код возврата SQL_SUCCESS_WITH_INFO, так как сообщения, отличные от 5701 и 5703, могут быть возвращены. Например, если драйвер соединяется с сервером, где запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с устаревшим каталогом хранимых процедур, одной из ошибок, возвращенные с помощью **SQLGetDiagRec** после SQL_SUCCESS_WITH_INFO, является:  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 Функция приложения для обработки ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключений должны вызывать **SQLGetDiagRec** пока не будет возвращено значение SQL_NO_DATA. Затем она должна реагировать на любые сообщения, отличные от с *pfNative* код 5701 или 5703.  
  
## <a name="see-also"></a>См. также  
 [Взаимодействие с SQL Server &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
