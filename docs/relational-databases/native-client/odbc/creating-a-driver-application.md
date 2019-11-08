---
title: Создание приложения драйвера SQL Server Native Client ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8960a75ed04e1e12f39a5f74002af6702b432480
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73761260"
---
# <a name="creating-a-driver-application"></a>Создание приложения драйвера
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В архитектуре ODBC имеется четыре компонента, которые выполняют следующие функции.  
  
|Компонент|Функция|  
|---------------|--------------|  
|Приложение|Вызывает функции ODBC для связи с источником данных ODBC, поставляет инструкции SQL и обрабатывает результирующие наборы.|  
|Диспетчер драйверов|Управляет связью между приложением и всеми драйверами ODBC, используемыми приложением.|  
|Драйвер|Обрабатывает вызовы всех функций ODBC из приложения, передает инструкции SQL из приложения в источник данных и возвращает результаты приложению. При необходимости драйвер переводит ODBC SQL из приложения в собственный SQL, используемый источником данных.|  
|Источник данных|Содержит все необходимые драйверу сведения для доступа к конкретному экземпляру данных в СУБД.|  
  
 Приложение, которое использует драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для взаимодействия с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], выполняет следующие задачи:  
  
-   соединяется с источником данных;  
  
-   отправляет инструкции SQL в источник данных;  
  
-   обрабатывает результаты инструкций из источника данных;  
  
-   обрабатывает сообщения об ошибках;  
  
-   Закрывает соединение с источником данных.  
  
 Более сложное приложение, написанное для драйвера ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], может также выполнять следующие задачи:  
  
-   использовать курсоры для управления расположением в результирующем наборе;  
  
-   запрашивать операции фиксации или отката для управления транзакциями;  
  
-   выполнять распределенные транзакции между двумя или несколькими серверами;  
  
-   запускать хранимые процедуры на удаленном сервере;  
  
-   вызывать функции каталога для запроса сведений об атрибутах результирующего набора;  
  
-   выполнять операции массового копирования;  
  
-   Операции управления большими данными (в столбцах**varchar (max)** , **nvarchar (max)** и **varbinary (max)** )  
  
-   использовать логику повторного соединения для облегчения отработки отказа при настроенном зеркальном отображении базы данных;  
  
-   записывать в журнал данные о производительности и о долго выполняемых запросах.  
  
 Для использования функций ODBC приложение на языке C или C++ должно включать файлы заголовка sql.h, sqlext.h и sqltypes.h. Для использования функций API-интерфейса установщика ODBC, приложение должно включать файл заголовка odbcinst.h. Приложение, использующее ODBC и Юникод, должно включать файл заголовка sqlucode.h. Приложения ODBC должны быть связаны с файлом odbc32.lib. Приложения ODBC, вызывающие функции API-интерфейса установщика ODBC, должны быть связаны с файлом odbccp32.lib. Эти файлы включены в пакет SDK платформы Windows.  
  
 Многие драйверы ODBC, в том числе драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], предлагают расширения ODBC для конкретного драйвера. Чтобы воспользоваться преимуществами расширений ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], приложение должно включать заголовочный файл sqlncli. h. Этот файл заголовка содержит следующее:  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] атрибуты подключения, относящиеся к драйверу ODBC для собственного клиента.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] атрибуты инструкции, относящиеся к драйверу ODBC для собственного клиента.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] атрибуты столбца, относящиеся к драйверу ODBC для собственного клиента.  
  
-   типы данных, относящиеся к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)];  
  
-   определяемые пользователем типы данных, относящиеся к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)];  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типы [SQLGetInfo](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md) , относящиеся к ДРАЙВЕРу ODBC для собственного клиента.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поля диагностики драйвера ODBC для собственного клиента.  
  
-   диагностические коды динамических функций, относящиеся к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)];  
  
-   определения типов C и C++ для собственных типов данных C, зависящие от [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (возвращаются, если столбцы привязаны к типу данных C SQL_C_BINARY);  
  
-   определение типа для структуры данных SQLPERF;  
  
-   макросы и прототипы массового копирования для поддержки API-интерфейса массового копирования через соединение ODBC;  
  
-   вызов функций API-интерфейса метаданных распределенного запроса для списков связанных серверов и их каталогов.  
  
 Любое приложение C C++ или ODBC, использующее функцию полного копирования драйвера ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], должно быть связано с файлом sqlncli11. lib. Приложения, вызывающие функции API-интерфейса метаданных распределенного запроса, также должны компоноваться с файлом sqlncli11.lib. Файлы sqlncli. h и sqlncli11. lib распространяются как часть средств разработчика [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Каталоги [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Include и Lib должны находиться в пути компилятора INCLUDE и LIB, как показано ниже:  
  
```  
LIB=c:\Program Files\Microsoft Data Access SDK 2.8\Libs\x86\lib;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Lib;  
INCLUDE=c:\Program Files\Microsoft Data Access SDK 2.8\inc;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Include;  
```  
  
 На раннем этапе разработки приложения необходимо решить, будет ли приложение нуждаться в нескольких одновременных вызовах ODBC. Существует два метода поддержки нескольких одновременных вызовов ODBC. Они описаны в оставшихся разделах этой темы. Дополнительные сведения см. в [справочнике программиста по ODBC](https://go.microsoft.com/fwlink/?LinkId=45250).  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Асинхронный режим и команда SQLCancel](../../../relational-databases/native-client/odbc/creating-a-driver-application-asynchronous-mode-and-sqlcancel.md)  
  
-   [Многопоточные приложения](../../../relational-databases/native-client/odbc/creating-a-driver-application-multithreaded-applications.md)  
  
## <a name="see-also"></a>См. также раздел  
 [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
