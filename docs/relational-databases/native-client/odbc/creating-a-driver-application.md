---
title: Создание драйвера приложение ODBC собственного клиента SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC, architecture
- SQL Server Native Client ODBC driver, creating applications
- ODBC function calls
- ODBC, header files
- ODBC applications
- ODBC applications, creating
- SQL Server Native Client ODBC driver, extensions
- applications [SQL Server Native Client]
- SQL Server Native Client ODBC driver, ODBC architecture
- extensions [ODBC]
- ODBC, driver extensions
- function calls [ODBC]
ms.assetid: c83c36e2-734e-4960-bc7e-92235910bc6f
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 61fa9d1d5d8fb848f508aef50c9e6d3ea996eaec
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-driver-application"></a>Создание приложения для драйвера
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  В архитектуре ODBC имеется четыре компонента, которые выполняют следующие функции.  
  
|Компонент|Функция|  
|---------------|--------------|  
|Приложение|Вызывает функции ODBC для связи с источником данных ODBC, поставляет инструкции SQL и обрабатывает результирующие наборы.|  
|Диспетчер драйверов|Управляет связью между приложением и всеми драйверами ODBC, используемыми приложением.|  
|Драйвер|Обрабатывает вызовы всех функций ODBC из приложения, передает инструкции SQL из приложения в источник данных и возвращает результаты приложению. При необходимости драйвер переводит ODBC SQL из приложения в собственный SQL, используемый источником данных.|  
|Источник данных|Содержит все необходимые драйверу сведения для доступа к конкретному экземпляру данных в СУБД.|  
  
 Приложение, использующее [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента для взаимодействия с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполняет следующие задачи:  
  
-   соединяется с источником данных;  
  
-   отправляет инструкции SQL в источник данных;  
  
-   обрабатывает результаты инструкций из источника данных;  
  
-   обрабатывает сообщения об ошибках;  
  
-   Закрывает соединение с источником данных.  
  
 Более сложные приложения, написанного для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента может также выполнять следующие задачи:  
  
-   использовать курсоры для управления расположением в результирующем наборе;  
  
-   запрашивать операции фиксации или отката для управления транзакциями;  
  
-   выполнять распределенные транзакции между двумя или несколькими серверами;  
  
-   запускать хранимые процедуры на удаленном сервере;  
  
-   вызывать функции каталога для запроса сведений об атрибутах результирующего набора;  
  
-   выполнять операции массового копирования;  
  
-   Управление большие объемы данных (**varchar(max)**, **nvarchar(max)**, и **varbinary(max)** столбцы) операций  
  
-   использовать логику повторного соединения для облегчения отработки отказа при настроенном зеркальном отображении базы данных;  
  
-   записывать в журнал данные о производительности и о долго выполняемых запросах.  
  
 Для использования функций ODBC приложение на языке C или C++ должно включать файлы заголовка sql.h, sqlext.h и sqltypes.h. Для использования функций API-интерфейса установщика ODBC, приложение должно включать файл заголовка odbcinst.h. Приложение, использующее ODBC и Юникод, должно включать файл заголовка sqlucode.h. Приложения ODBC должны быть связаны с файлом odbc32.lib. Приложения ODBC, вызывающие функции API-интерфейса установщика ODBC, должны быть связаны с файлом odbccp32.lib. Эти файлы включены в пакет SDK платформы Windows.  
  
 Многие драйверы ODBC, включая [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента предоставляют расширения ODBC драйвера. Чтобы воспользоваться преимуществами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] расширениями драйвера ODBC для собственного клиента, приложение должно включать файл заголовка sqlncli.h. Этот файл заголовка содержит следующее:  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Атрибуты соединения драйвера собственного клиента ODBC.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Атрибуты инструкции драйвером собственного клиента ODBC.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Атрибуты столбца драйвера собственного клиента ODBC.  
  
-   типы данных, относящиеся к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)];  
  
-   определяемые пользователем типы данных, относящиеся к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)];  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственного клиента ODBC-драйвером [SQLGetInfo](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md) типов.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственный клиент диагностические поля драйвера ODBC.  
  
-   диагностические коды динамических функций, относящиеся к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)];  
  
-   определения типов C и C++ для собственных типов данных C, зависящие от [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (возвращаются, если столбцы привязаны к типу данных C SQL_C_BINARY);  
  
-   определение типа для структуры данных SQLPERF;  
  
-   макросы и прототипы массового копирования для поддержки API-интерфейса массового копирования через соединение ODBC;  
  
-   вызов функций API-интерфейса метаданных распределенного запроса для списков связанных серверов и их каталогов.  
  
 Любое приложение C или C++ ODBC, использующее функцию массового копирования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента должны быть связаны с файлом sqlncli11.lib. Приложения, вызывающие функции API-интерфейса метаданных распределенного запроса, также должны компоноваться с файлом sqlncli11.lib. Файлы sqlncli.h и sqlncli11.lib поставляются в составе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] средств разработчика. Каталоги [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Include и Lib должны находиться в пути компилятора INCLUDE и LIB, как показано ниже:  
  
```  
LIB=c:\Program Files\Microsoft Data Access SDK 2.8\Libs\x86\lib;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Lib;  
INCLUDE=c:\Program Files\Microsoft Data Access SDK 2.8\inc;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Include;  
```  
  
 На раннем этапе разработки приложения необходимо решить, будет ли приложение нуждаться в нескольких одновременных вызовах ODBC. Существует два метода поддержки нескольких одновременных вызовов ODBC. Они описаны в оставшихся разделах этой темы. Дополнительные сведения см. в разделе [справочнике программиста ODBC](http://go.microsoft.com/fwlink/?LinkId=45250).  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Асинхронный режим и команда SQLCancel](../../../relational-databases/native-client/odbc/creating-a-driver-application-asynchronous-mode-and-sqlcancel.md)  
  
-   [Многопоточные приложения](../../../relational-databases/native-client/odbc/creating-a-driver-application-multithreaded-applications.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server & #40; ODBC & #41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
