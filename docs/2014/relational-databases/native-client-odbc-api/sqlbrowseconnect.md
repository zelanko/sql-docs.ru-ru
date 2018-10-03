---
title: SQLBrowseConnect | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBrowseConnect function
ms.assetid: 57faf388-c7ca-4696-9845-34e0a10cc5f7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5300285872c0c03ce25410ba0bfd636c7ccf6bca
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48208538"
---
# <a name="sqlbrowseconnect"></a>SQLBrowseConnect
  **SQLBrowseConnect** использует ключевые слова, которые можно разделить на три уровня сведений о соединении. Для каждого ключевого слова в следующей таблице указано, возвращается ли список допустимых значений и является ли ключевое слово необязательным.  
  
## <a name="level-1"></a>уровне 1  
  
|Ключевое слово|Возвращает список?|Является необязательным?|Описание|  
|-------------|--------------------|---------------|-----------------|  
|DSN|Недоступно|Нет|Имя источника данных, возвращенных **SQLDataSources**. Ключевое слово DSN нельзя использовать, если используется ключевое слово DRIVER.|  
|DRIVER|Недоступно|Нет|Microsoft® [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя драйвера ODBC для собственного клиента {[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11}. Ключевое слово DRIVER нельзя использовать, если используется ключевое слово DSN.|  
  
## <a name="level-2"></a>Уровень 2  
  
|Ключевое слово|Возвращает список?|Является необязательным?|Описание|  
|-------------|--------------------|---------------|-----------------|  
|SERVER|Да|Нет|Имя сервера источника данных в сети. В качестве сервера можно ввести термин «(local)»; в этом случае можно использовать локальную копию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], даже если это не сетевая версия.|  
|UID|Нет|Да|Идентификатор входа пользователя.|  
|PWD|Нет|Да (зависит от пользователя)|Определяемый пользователем пароль.|  
|APP|Нет|Да|Имя приложения, вызывающего **SQLBrowseConnect**.|  
|WSID|Нет|Да|Идентификатор рабочей станции. Обычно это сетевое имя компьютера, на котором работает приложение.|  
  
## <a name="level-3"></a>Уровень 3  
  
|Ключевое слово|Возвращает список?|Является необязательным?|Описание|  
|-------------|--------------------|---------------|-----------------|  
|DATABASE|Да|Да|Имя базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|LANGUAGE|Да|Да|Национальный язык, используемый [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 **SQLBrowseConnect** не учитывает значения ключевых слов DATABASE и LANGUAGE, хранящиеся в определениях источника данных ODBC. Если базы данных или языка, указанного в строке подключения указано **SQLBrowseConnect** является недопустимым, **SQLBrowseConnect** возвращает SQL_NEED_DATA и атрибуты соединения уровня 3.  
  
 Следующие атрибуты, которые устанавливаются с помощью вызова [SQLSetConnectAttr](sqlsetconnectattr.md), определяют результирующий набор, возвращаемый **SQLBrowseConnect**.  
  
|attribute|Описание|  
|---------------|-----------------|  
|SQL_COPT_SS_BROWSE_CONNECT|Если оно установлено значение SQL_MORE_INFO_YES, **SQLBrowseConnect** возвращает расширенную строку свойств сервера.<br /><br /> Ниже приведен пример расширенной строки, возвращаемые **SQLBrowseConnect**: Имя_сервера\имя_экземпляра; Кластеризованный: нет; Версия: 8.00.131<br /><br /> В этой строке различные порции данных о сервере разделяются точками с запятой. Для разделения различных экземпляров сервера используйте запятые.|  
|SQL_COPT_SS_BROWSE_SERVER|Если указано имя сервера, **SQLBrowseConnect** возвращает сведения об указанном сервере. Если для SQL_COPT_SS_BROWSE_SERVER задано значение NULL, **SQLBrowseConnect** возвращает сведения обо всех серверах в домене.<br /><br /> Из-за проблем с сетью **SQLBrowseConnect** может не получить своевременный ответ от всех серверов. Поэтому возвращаемый список серверов может отличаться от запроса к запросу.|  
|SQL_COPT_SS_BROWSE_CACHE_DATA|Если атрибут SQL_COPT_SS_BROWSE_CACHE_DATA имеет значение SQL_CACHE_DATA_YES, то в случае, когда длина буфера недостаточна для размещения результата, можно получать данные фрагментами. Эта длина задается в качестве аргумента BufferLength SQLBrowseConnect.<br /><br /> Если доступны дополнительные данные, возвращается значение SQL_NEED_DATA. Если нет неполученных данных, возвращается значение SQL_SUCCESS.<br /><br /> По умолчанию задано значение SQL_CACHE_DATA_NO.|  
  
## <a name="sqlbrowseconnect-support-for-high-availability-disaster-recovery"></a>Поддержка высокого уровня доступности и аварийного восстановления SQLBrowseConnect  
 Дополнительные сведения об использовании **SQLBrowseConnect** для подключения к [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] кластера, см. в разделе [SQL Server Native Client Support для высокого уровня доступности и аварийного восстановления](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqlbrowseconnect-support-for-service-principal-names-spns"></a>Поддержка функции SQLBrowseConnect для имен участников-служб  
 При открытии соединения собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задает SQL_COPT_SS_MUTUALLY_AUTHENTICATED и SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD метод проверки подлинности, используемый для открытия соединения.  
  
 Дополнительные сведения об именах SPN см. в разделе [имена участников-служб &#40;имена участников-служб&#41; в клиентских соединениях &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="change-history"></a>Журнал изменений  
  
|Обновленное содержимое|  
|---------------------|  
|Добавлена документация по SQL_COPT_SS_BROWSE_CACHE_DATA.|  
  
## <a name="see-also"></a>См. также  
 [Функция SQLBrowseConnect](http://go.microsoft.com/fwlink/?LinkId=59329)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
