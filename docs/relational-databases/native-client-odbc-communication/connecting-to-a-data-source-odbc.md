---
title: "Соединение с источником данных (ODBC) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-communication
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f6be6bcf54b4db444e78d72a5321457c0eb373c2
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="connecting-to-a-data-source-odbc"></a>Соединение с источником данных (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  После определения среды и дескрипторов соединения, а также установки любых атрибутов соединения приложение устанавливает соединение с источником данных или драйвером. Существует три функции, которые можно использовать для установки соединения:  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLBrowseConnect**  
  
 Дополнительные сведения о подключении к источнику данных, включая различные доступные параметры строки соединения, в разделе [с помощью ключевых слов строки подключения с собственным клиентом SQL Server](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
## <a name="sqlconnect"></a>SQLConnect  
 **SQLConnect** является простейшей функцией соединения. Она принимает три параметра: имя источника данных, идентификатор пользователя и пароль. Используйте **SQLConnect** при эти три параметра содержат всю информацию, необходимую для подключения к базе данных. Для этого необходимо создать список источников данных, используя **SQLDataSources**; запрашивать пользователя для источника данных, идентификатор пользователя и пароль; а затем вызвать **SQLConnect**.  
  
 **SQLConnect** предполагается, что имя источника данных, идентификатор пользователя и пароль достаточны для подключения к источнику данных и, источник данных ODBC содержит все сведения, необходимы драйверу ODBC для подключения. В отличие от [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) и [SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md), **SQLConnect** не использует строку подключения.  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
 **SQLDriverConnect** используется, когда требуется больше сведений, чем имя источника данных, идентификатор пользователя и пароль. Один из параметров для **SQLDriverConnect** представляет собой строку соединения, содержащий сведения, относящиеся к драйверу. Можно использовать **SQLDriverConnect** вместо **SQLConnect** по следующим причинам:  
  
-   для указания специфической для драйвера информации во время подключения;  
  
-   для запроса, который драйвер направляет пользователю для получения информации о соединении;  
  
-   для соединения без использования источника данных ODBC.  
  
 **SQLDriverConnect** строка подключения содержит ряд пар значение ключевого слова, указывающие всех сведений о соединении, поддерживаются драйвером ODBC. Каждый драйвер поддерживает стандартные ключевые слова ODBC (DSN, FILEDSN, DRIVER, UID, PWD и SAVEFILE) в дополнение к специальным ключевым словам драйвера для указания всей информации о соединении, поддерживаемой драйвером. **SQLDriverConnect** может использоваться для подключения без источника данных. Например, приложение, предназначенное для установки подключения к экземпляру компонента «Без DSN» [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно вызвать **SQLDriverConnect** со строкой соединения, определяющий идентификатор имени входа, пароль, сетевую библиотеку, имя сервера, чтобы Подключитесь и база данных для использования по умолчанию.  
  
 При использовании **SQLDriverConnect**, существует два варианта для подсказки пользователю необходимой для соединения информации:  
  
-   Диалоговое окно приложения  
  
     Можно создать диалоговое окно приложения, запрашивает сведения о соединении, а затем вызывает **SQLDriverConnect** с дескриптором окна NULL и *DriverCompletion* равным SQL_DRIVER_NOPROMPT. Эти параметры предотвращают открытие драйвером ODBC собственного диалогового окна. Этот метод используется, когда важно управлять пользовательским интерфейсом приложения.  
  
-   Диалоговое окно драйвера  
  
     Можно запрограммировать приложение на передачу допустимого дескриптора окна в **SQLDriverConnect** и задайте *DriverCompletion* параметр SQL_DRIVER_COMPLETE, SQL_DRIVER_PROMPT или SQL_DRIVER_COMPLETE_ Обязательно. Затем драйвер формирует диалоговое окно для получения от пользователя информации о соединении. Этот метод упрощает код приложения.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
 **SQLBrowseConnect**, таких как **SQLDriverConnect**, использует строку подключения. Однако с помощью **SQLBrowseConnect**, приложение может создать полную строку подключения итеративного с источником данных во время выполнения. Это позволяет приложению:  
  
-   строить собственные диалоговые окна для запроса этой информации, сохраняя таким образом управление своим пользовательским интерфейсом;  
  
-   просматривать систему в поисках источников данных, которые может использовать конкретный драйвер, возможно, за несколько шагов.  
  
     Например, пользователь может сначала просмотреть серверы в сети, а после выбора сервера с помощью драйвера просмотреть доступные базы данных этого сервера.  
  
 Когда **SQLBrowseConnect** завершения удачного соединения, он возвращает строку подключения, который может использоваться при последующих вызовах **SQLDriverConnect**.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента всегда возвращает значение SQL_SUCCESS_WITH_INFO на удачный вызов **SQLConnect**, **SQLDriverConnect**, или **SQLBrowseConnect**. Если приложение ODBC вызывает **SQLGetDiagRec** после получения SQL_SUCCESS_WITH_INFO, он может получить следующие сообщения:  
  
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
  
 Можно не обрабатывать сообщения 5701 и 5703; они всего лишь информационные. Однако не следует пропускать код возврата SQL_SUCCESS_WITH_INFO, так как сообщения, отличные от 5701 и 5703, могут быть возвращены. Например, если драйвер подключается к серверу, где запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с устаревшим каталогом хранимых процедур, одной из ошибок, возвращенные с помощью **SQLGetDiagRec** после SQL_SUCCESS_WITH_INFO, является:  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 Функция приложения для обработки ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключений следует вызывать **SQLGetDiagRec** пока не будет возвращено значение SQL_NO_DATA. Затем она должна реагировать на любые сообщения, кроме тех, которые с *pfNative* код 5701 или 5703.  
  
## <a name="see-also"></a>См. также:  
 [Взаимодействие с SQL Server &#40; ODBC &#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
