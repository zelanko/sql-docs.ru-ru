---
title: Создание приложения
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4e65eaac59bcc16e123bda3e47af29dc4a836ce5
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388390"
---
# <a name="creating-a-driver-application"></a>Создание приложения драйвера
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В архитектуре ODBC имеется четыре компонента, которые выполняют следующие функции.  
  
|Компонент|Компонент|  
|---------------|--------------|  
|Приложение|Вызывает функции ODBC для связи с источником данных ODBC, поставляет инструкции SQL и обрабатывает результирующие наборы.|  
|Диспетчер драйверов|Управляет связью между приложением и всеми драйверами ODBC, используемыми приложением.|  
|Драйвер|Обрабатывает вызовы всех функций ODBC из приложения, передает инструкции SQL из приложения в источник данных и возвращает результаты приложению. При необходимости драйвер переводит ODBC SQL из приложения в собственный SQL, используемый источником данных.|  
|Источник данных|Содержит все необходимые драйверу сведения для доступа к конкретному экземпляру данных в СУБД.|  
  
 Приложение, используюваекоторое [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвером Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC для связи с экземпляром выполнения следующих задач:  
  
-   соединяется с источником данных;  
  
-   отправляет инструкции SQL в источник данных;  
  
-   обрабатывает результаты инструкций из источника данных;  
  
-   обрабатывает сообщения об ошибках;  
  
-   Закрывает соединение с источником данных.  
  
 Более сложное приложение, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] написанное для драйвера ODBC Native Client, также может выполнять следующие задачи:  
  
-   использовать курсоры для управления расположением в результирующем наборе;  
  
-   запрашивать операции фиксации или отката для управления транзакциями;  
  
-   выполнять распределенные транзакции между двумя или несколькими серверами;  
  
-   запускать хранимые процедуры на удаленном сервере;  
  
-   вызывать функции каталога для запроса сведений об атрибутах результирующего набора;  
  
-   выполнять операции массового копирования;  
  
-   Управление большими данными **(varchar(max)**, **nvarchar(max)** и **варбинарными (макс)** столбцов)  
  
-   использовать логику повторного соединения для облегчения отработки отказа при настроенном зеркальном отображении базы данных;  
  
-   записывать в журнал данные о производительности и о долго выполняемых запросах.  
  
 Для использования функций ODBC приложение на языке C или C++ должно включать файлы заголовка sql.h, sqlext.h и sqltypes.h. Для использования функций API-интерфейса установщика ODBC, приложение должно включать файл заголовка odbcinst.h. Приложение, использующее ODBC и Юникод, должно включать файл заголовка sqlucode.h. Приложения ODBC должны быть связаны с файлом odbc32.lib. Приложения ODBC, вызывающие функции API-интерфейса установщика ODBC, должны быть связаны с файлом odbccp32.lib. Эти файлы включены в пакет SDK платформы Windows.  
  
 Многие драйверы ODBC, включая драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC, предлагают специальные расширения ODBC для водителей. Чтобы воспользоваться [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] преимуществами расширения драйвера Native Client ODBC, приложение должно включать файл заголовка sqlncli.h. Этот файл заголовка содержит следующее:  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Атрибуты подключения к драйверу NATIVE Client ODBC.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Атрибуты оператора, конкретного драйвера Native Client ODBC.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Атрибуты столбца ODBC native Client ODBC.  
  
-   типы данных, относящиеся к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)];  
  
-   определяемые пользователем типы данных, относящиеся к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)];  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Родная клиентская компания ODBC, специфичная для драйверов [типа SLGetInfo.](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md)  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Поля диагностики драйверов NATIVE Client ODBC.  
  
-   диагностические коды динамических функций, относящиеся к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)];  
  
-   определения типов C и C++ для собственных типов данных C, зависящие от [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (возвращаются, если столбцы привязаны к типу данных C SQL_C_BINARY);  
  
-   определение типа для структуры данных SQLPERF;  
  
-   макросы и прототипы массового копирования для поддержки API-интерфейса массового копирования через соединение ODBC;  
  
-   вызов функций API-интерфейса метаданных распределенного запроса для списков связанных серверов и их каталогов.  
  
 Любое приложение C или C' ODBC, использующее функцию копирования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] навалом драйвера Native Client ODBC, должно быть связано с файлом sqlncli11.lib. Приложения, вызывающие функции API-интерфейса метаданных распределенного запроса, также должны компоноваться с файлом sqlncli11.lib. Файлы sqlncli.h и sqlncli11.lib распространяются [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] как часть инструментов разработчика. Каталоги [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Include и Lib должны находиться в пути компилятора INCLUDE и LIB, как показано ниже:  
  
```  
LIB=c:\Program Files\Microsoft Data Access SDK 2.8\Libs\x86\lib;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Lib;  
INCLUDE=c:\Program Files\Microsoft Data Access SDK 2.8\inc;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Include;  
```  
  
 На раннем этапе разработки приложения необходимо решить, будет ли приложение нуждаться в нескольких одновременных вызовах ODBC. Существует два метода поддержки нескольких одновременных вызовов ODBC. Они описаны в оставшихся разделах этой темы. Для получения дополнительной [информации](https://go.microsoft.com/fwlink/?LinkId=45250)см.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Асинхронный режим и команда SQLCancel](../../../relational-databases/native-client/odbc/creating-a-driver-application-asynchronous-mode-and-sqlcancel.md)  
  
-   [Многопоточные приложения](../../../relational-databases/native-client/odbc/creating-a-driver-application-multithreaded-applications.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
