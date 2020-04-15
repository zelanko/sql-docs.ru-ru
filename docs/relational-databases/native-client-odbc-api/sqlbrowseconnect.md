---
title: СЗЛBrowseConnect (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBrowseConnect function
ms.assetid: 57faf388-c7ca-4696-9845-34e0a10cc5f7
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3a2b6d1b5bdc722a362c5ed67bff611602a860e2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302665"
---
# <a name="sqlbrowseconnect"></a>SQLBrowseConnect
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **В sLBrowseConnect** используются ключевые слова, которые можно разделить на три уровня информации о подключении. Для каждого ключевого слова в следующей таблице указано, возвращается ли список допустимых значений и является ли ключевое слово необязательным.  
  
## <a name="level-1"></a>уровне 1  
  
|Ключевое слово|Возвращает список?|Является необязательным?|Описание|  
|-------------|--------------------|---------------|-----------------|  
|DSN|Н/Д|нет|Имя источника данных, возвращенного **S'LDataSources**. Ключевое слово DSN нельзя использовать, если используется ключевое слово DRIVER.|  
|DRIVER|Н/Д|нет|Имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвера коренных клиентов[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Microsoft® — «Родной клиент 11». Ключевое слово DRIVER нельзя использовать, если используется ключевое слово DSN.|  
  
## <a name="level-2"></a>Уровень 2  
  
|Ключевое слово|Возвращает список?|Является необязательным?|Описание|  
|-------------|--------------------|---------------|-----------------|  
|SERVER|Да|нет|Имя сервера источника данных в сети. В качестве сервера можно ввести термин «(local)»; в этом случае можно использовать локальную копию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], даже если это не сетевая версия.|  
|ИД пользователя|нет|Да|Идентификатор входа пользователя.|  
|PWD|нет|Да (зависит от пользователя)|Определяемый пользователем пароль.|  
|APP|нет|Да|Название приложения, вызываемое **s'LBrowseConnect**.|  
|WSID|нет|Да|Идентификатор рабочей станции. Обычно это сетевое имя компьютера, на котором работает приложение.|  
  
## <a name="level-3"></a>Level 3  
  
|Ключевое слово|Возвращает список?|Является необязательным?|Описание|  
|-------------|--------------------|---------------|-----------------|  
|DATABASE|Да|Да|Имя базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|LANGUAGE|Да|Да|Национальный язык, используемый [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 **S'LBrowseConnect** игнорирует значения ключевых слов DATABASE и LANGUAGE, хранящиеся в определениях источников данных ODBC. Если база данных или язык, указанный в строке подключения, передаваемый в **s'LBrowseConnect,** недействительны, **S'LBrowseConnect** возвращается SQL_NEED_DATA и атрибуты соединения уровня 3.  
  
 Следующие атрибуты, которые устанавливаются по телефону [S'LSetConnectAttr,](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)определяют набор результатов, возвращенный **S'LBrowseConnect.**  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|SQL_COPT_SS_BROWSE_CONNECT|Если он настроен на SQL_MORE_INFO_YES, **S'LBrowseConnect** возвращает расширенную строку свойств сервера.<br /><br /> Ниже приводится пример расширенной строки, возвращенной **S'LBrowseConnect:**<br /><br /> <br /><br /> `ServerName\InstanceName;Clustered:No;Version:8.00.131`<br /><br /> <br /><br /> В этой строке различные порции данных о сервере разделяются точками с запятой. Для разделения различных экземпляров сервера используйте запятые.|  
|SQL_COPT_SS_BROWSE_SERVER|Если указано имя сервера, **S'LBrowseConnect** вернет информацию для указанного сервера. Если SQL_COPT_SS_BROWSE_SERVER установлена на NULL, **S'LBrowseConnect** возвращает информацию для всех серверов в домене.<br /><br /> <br /><br /> Обратите внимание, что из-за проблем с **сетью, S'LBrowseConnect** может не получить своевременного ответа от всех серверов. Поэтому возвращаемый список серверов может отличаться от запроса к запросу.|  
|SQL_COPT_SS_BROWSE_CACHE_DATA|Если атрибут SQL_COPT_SS_BROWSE_CACHE_DATA имеет значение SQL_CACHE_DATA_YES, то в случае, когда длина буфера недостаточна для размещения результата, можно получать данные фрагментами. Эта длина указана в аргументе BufferLength в аргумент s'LBrowseConnect.<br /><br /> Если доступны дополнительные данные, возвращается значение SQL_NEED_DATA. Если нет неполученных данных, возвращается значение SQL_SUCCESS.<br /><br /> По умолчанию задано значение SQL_CACHE_DATA_NO.|  
  
## <a name="sqlbrowseconnect-support-for-high-availability-disaster-recovery"></a>Поддержка высокого уровня доступности и аварийного восстановления SQLBrowseConnect  
 Для получения более подробной информации об [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] использовании **s'LBrowseConnect** для подключения к кластеру, [SQL Server Native Client Support for High Availability, Disaster Recovery](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)см.  
  
## <a name="sqlbrowseconnect-support-for-service-principal-names-spns"></a>Поддержка функции SQLBrowseConnect для имен участников-служб  
 При открытии соединения собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задает SQL_COPT_SS_MUTUALLY_AUTHENTICATED и SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD метод проверки подлинности, используемый для открытия соединения.  
  
 Для получения дополнительной информации о SPNs см [&#41;&#40;&#41; &#40;. ](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)  
  
## <a name="change-history"></a>Журнал изменений  
  
|Обновленное содержимое|  
|---------------------|  
|Добавлена документация по SQL_COPT_SS_BROWSE_CACHE_DATA.|  
  
## <a name="see-also"></a>См. также:  
 [Функция S'LBrowseConnect](https://go.microsoft.com/fwlink/?LinkId=59329)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
