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
ms.openlocfilehash: d9cb9439dd76c636df46b8ac3d737d79415b5ea5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63067674"
---
# <a name="sqlbrowseconnect"></a>SQLBrowseConnect
  **SQLBrowseConnect** использует ключевые слова, которые можно классифицировать по трем уровням сведений о соединении. Для каждого ключевого слова в следующей таблице указано, возвращается ли список допустимых значений и является ли ключевое слово необязательным.  
  
## <a name="level-1"></a>уровне 1  
  
|Ключевое слово|Возвращает список?|Является необязательным?|Описание|  
|-------------|--------------------|---------------|-----------------|  
|DSN|Н/Д|Нет|Имя источника данных, возвращаемого функцией **SQLDataSources**. Ключевое слово DSN нельзя использовать, если используется ключевое слово DRIVER.|  
|DRIVER|Н/Д|Нет|Microsoft?? [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Имя драйвера ODBC для собственного клиента:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] {Native Client 11}. Ключевое слово DRIVER нельзя использовать, если используется ключевое слово DSN.|  
  
## <a name="level-2"></a>Уровень 2  
  
|Ключевое слово|Возвращает список?|Является необязательным?|Описание|  
|-------------|--------------------|---------------|-----------------|  
|SERVER|Да|Нет|Имя сервера источника данных в сети. В качестве сервера можно ввести термин «(local)»; в этом случае можно использовать локальную копию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], даже если это не сетевая версия.|  
|ИД пользователя|Нет|Да|Идентификатор входа пользователя.|  
|PWD|Нет|Да (зависит от пользователя)|Определяемый пользователем пароль.|  
|APP|Нет|Да|Имя приложения, вызывающего **SQLBrowseConnect**.|  
|WSID|Нет|Да|Идентификатор рабочей станции. Обычно это сетевое имя компьютера, на котором работает приложение.|  
  
## <a name="level-3"></a>Level 3  
  
|Ключевое слово|Возвращает список?|Является необязательным?|Описание|  
|-------------|--------------------|---------------|-----------------|  
|DATABASE|Да|Да|Имя базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|LANGUAGE|Да|Да|Национальный язык, используемый [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 **SQLBrowseConnect** игнорирует значения ключевых слов базы данных и языка, которые хранятся в определениях источников данных ODBC. Если база данных или язык, указанные в строке соединения, переданной в **SQLBrowseConnect** , являются недопустимыми, **SQLBrowseConnect** возвращает SQL_NEED_DATA и атрибуты подключения уровня 3.  
  
 Следующие атрибуты, которые устанавливаются путем вызова [SQLSetConnectAttr](sqlsetconnectattr.md), определяют результирующий набор, возвращаемый **SQLBrowseConnect**.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|SQL_COPT_SS_BROWSE_CONNECT|Если задано значение SQL_MORE_INFO_YES, **SQLBrowseConnect** возвращает расширенную строку свойств сервера.<br /><br /> Ниже приведен пример расширенной строки, возвращаемой функцией **SQLBrowseConnect**: ServerName\InstanceName; Кластеризованный: нет; Версия: 8.00.131<br /><br /> В этой строке различные порции данных о сервере разделяются точками с запятой. Для разделения различных экземпляров сервера используйте запятые.|  
|SQL_COPT_SS_BROWSE_SERVER|Если указано имя сервера, **SQLBrowseConnect** возвратит сведения для указанного сервера. Если SQL_COPT_SS_BROWSE_SERVER имеет значение NULL, **SQLBrowseConnect** возвращает сведения обо всех серверах в домене.<br /><br /> Из-за проблем в сети **SQLBrowseConnect** может не получить своевременный ответ от всех серверов. Поэтому возвращаемый список серверов может отличаться от запроса к запросу.|  
|SQL_COPT_SS_BROWSE_CACHE_DATA|Если атрибут SQL_COPT_SS_BROWSE_CACHE_DATA имеет значение SQL_CACHE_DATA_YES, то в случае, когда длина буфера недостаточна для размещения результата, можно получать данные фрагментами. Эта длина указывается в аргументе BufferLength для SQLBrowseConnect.<br /><br /> Если доступны дополнительные данные, возвращается значение SQL_NEED_DATA. Если нет неполученных данных, возвращается значение SQL_SUCCESS.<br /><br /> По умолчанию задано значение SQL_CACHE_DATA_NO.|  
  
## <a name="sqlbrowseconnect-support-for-high-availability-disaster-recovery"></a>Поддержка высокого уровня доступности и аварийного восстановления SQLBrowseConnect  
 Дополнительные сведения об использовании **SQLBrowseConnect** для подключения к [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] кластеру см. в разделе [Поддержка высокой доступности и аварийного восстановления в SQL Server Native Client](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqlbrowseconnect-support-for-service-principal-names-spns"></a>Поддержка функции SQLBrowseConnect для имен участников-служб  
 При открытии соединения собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задает SQL_COPT_SS_MUTUALLY_AUTHENTICATED и SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD метод проверки подлинности, используемый для открытия соединения.  
  
 Дополнительные сведения о SPN см. [в статье имена субъектов-служб &#40;имен участников-служб&#41; в клиентских подключениях &#40;&#41;ODBC ](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="change-history"></a>Журнал изменений  
  
|Обновленное содержимое|  
|---------------------|  
|Добавлена документация по SQL_COPT_SS_BROWSE_CACHE_DATA.|  
  
## <a name="see-also"></a>См. также  
 [Функция SQLBrowseConnect](https://go.microsoft.com/fwlink/?LinkId=59329)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
