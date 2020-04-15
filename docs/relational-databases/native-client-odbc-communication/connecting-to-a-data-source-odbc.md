---
title: Подключение к источнику данных (ODBC) Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ae59e0bdb005d296341970f4582100b15a0dfdf7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307735"
---
# <a name="connecting-to-a-data-source-odbc"></a>Соединение с источником данных (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  После определения среды и дескрипторов соединения, а также установки любых атрибутов соединения приложение устанавливает соединение с источником данных или драйвером. Существует три функции, которые можно использовать для установки соединения:  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLBrowseConnect**  
  
 Для получения дополнительной информации о подключении к источнику данных, включая различные варианты строки соединения, [см.](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
## <a name="sqlconnect"></a>SQLConnect  
 Самой простой функцией соединения является **S'LConnect.** Она принимает три параметра: имя источника данных, идентификатор пользователя и пароль. Используйте **S'LConnect,** когда эти три параметра содержат всю информацию, необходимую для подключения к базе данных. Для этого создайте список источников данных с помощью **S'LDataSources;** запрос пользователя на источник данных, идентификатор пользователя и пароль; а затем позвоните по **s-LConnect**.  
  
 **SLConnect** предполагает, что имя источника данных, идентификатор пользователя и пароль достаточны для подключения к источнику данных и что источник данных ODBC содержит всю другую информацию, необходимую водителю ODBC для подключения. В отличие от [S'LDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) и [S'LBrowseConnect,](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md) **S'LConnect** не использует строку подключения.  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
 **SLDriverConnect** используется, когда требуется больше информации, чем имя источника данных, идентификатор пользователя и пароль. Одним из **параметров, наблюдаванных в sLDriverConnect,** является строка соединения, содержащая информацию о конкретной драйвере. Вместо **sLConnect** можно использовать **s'LDriverConnect** по следующим причинам:  
  
-   для указания специфической для драйвера информации во время подключения;  
  
-   для запроса, который драйвер направляет пользователю для получения информации о соединении;  
  
-   для соединения без использования источника данных ODBC.  
  
 Строка подключения **S'LDriverConnect** содержит ряд пар с ключевыми словами, которые указывают всю информацию о подключении, поддерживаемую драйвером ODBC. Каждый драйвер поддерживает стандартные ключевые слова ODBC (DSN, FILEDSN, DRIVER, UID, PWD и SAVEFILE) в дополнение к специальным ключевым словам драйвера для указания всей информации о соединении, поддерживаемой драйвером. **Для** подключения без источника данных можно использовать для подключения. Например, приложение, предназначенное для подключения к экземпляру "DSN-less", [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может **вызыватьs s'LDriverConnect** со строкой подключения, определяющей идентификатор входа, пароль, сетевую библиотеку, имя сервера для подключения и базу данных по умолчанию для использования.  
  
 При **использовании S'LDriverConnect**существует два варианта, побуждающих пользователя к любой необходимой информации о подключении:  
  
-   Диалоговое окно приложения  
  
     Можно создать диалоговую коробку приложений, которая подскажет информацию о подключении, а затем вызвать **S'LDriverConnect** с ручкой окна NULL и *DriverCompletion,* установленным для SQL_DRIVER_NOPROMPT. Эти параметры предотвращают открытие драйвером ODBC собственного диалогового окна. Этот метод используется, когда важно управлять пользовательским интерфейсом приложения.  
  
-   Диалоговое окно драйвера  
  
     Вы можете закодировать приложение, чтобы передать действительную ручку окна в **S'LDriverConnect** и установить параметр *DriverCompletion* для SQL_DRIVER_COMPLETE, SQL_DRIVER_PROMPT или SQL_DRIVER_COMPLETE_REQUIRED. Затем драйвер формирует диалоговое окно для получения от пользователя информации о соединении. Этот метод упрощает код приложения.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
 **S'LBrowseConnect**, как **и S'LDriverConnect**, использует строку соединения. Тем не менее, с помощью **S'LBrowseConnect,** приложение может построить полную строку соединения итеративно с источником данных во время выполнения. Это позволяет приложению:  
  
-   строить собственные диалоговые окна для запроса этой информации, сохраняя таким образом управление своим пользовательским интерфейсом;  
  
-   просматривать систему в поисках источников данных, которые может использовать конкретный драйвер, возможно, за несколько шагов.  
  
     Например, пользователь может сначала просмотреть серверы в сети, а после выбора сервера с помощью драйвера просмотреть доступные базы данных этого сервера.  
  
 Когда **S'LBrowseConnect** завершает успешное подключение, он возвращает строку соединения, которая может быть использована при последующих вызовах в **S'LDriverConnect.**  
  
 Водитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC всегда возвращается SQL_SUCCESS_WITH_INFO на успешный **S'LConnect,** **S'LDriverConnect**, или **S'LBrowseConnect**. Когда приложение ODBC вызывает **s'LGetDiagRec** после получения SQL_SUCCESS_WITH_INFO, оно может получать следующие сообщения:  
  
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
  
 Можно не обрабатывать сообщения 5701 и 5703; они всего лишь информационные. Однако не следует пропускать код возврата SQL_SUCCESS_WITH_INFO, так как сообщения, отличные от 5701 и 5703, могут быть возвращены. Например, если драйвер подключается к серверу, работающего [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляром с устаревшими процедурами хранения каталога, одна из ошибок, возвращенных через **S'LGetDiagRec** после SQL_SUCCESS_WITH_INFO:  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 Функция обработки ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приложения для подключений должна **вызыватьs s'LGetDiagRec** до тех пор, пока оно не вернется SQL_NO_DATA. Затем он должен действовать на любые сообщения, кроме тех, с *кодом pfNative* 5701 или 5703.  
  
## <a name="see-also"></a>См. также:  
 [Общение с сервером &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
