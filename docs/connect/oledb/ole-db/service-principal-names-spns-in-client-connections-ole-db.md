---
title: Имена участника-службы (SPN) в клиентских соединениях (OLE DB) | Документы Microsoft
description: Имена участника-службы (SPN) в клиентских соединениях (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6593f30709c2db1201962dc37b4e3c133265feac
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="service-principal-names-spns-in-client-connections-ole-db"></a>Имена участника-службы в клиентских соединениях (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


  В этом разделе описываются свойства OLE DB и функции элементов, поддерживающие имена участника-службы (SPN) в клиентских приложениях. Дополнительные сведения об именах SPN в клиентских приложениях см. в разделе [имени участника-службы &#40;имени участника-службы&#41; поддержка в клиентских соединениях](../../oledb/features/service-principal-name-spn-support-in-client-connections.md). Пример см. в разделе [встроенную проверку подлинности Kerberos &#40;OLE DB&#41;](../../oledb/ole-db-how-to/integrated-kerberos-authentication-ole-db.md).  
  
## <a name="provider-initialization-string-keywords"></a>Ключевые слова строки инициализации поставщика  
 Следующие ключевые слова строки инициализации поставщика поддерживают имена участников-служб в приложениях OLE DB. В следующей таблице значения в столбце ключевых слов используются для поставщика строка IDBInitialize::Initialize. Значения в столбце описания используются в строках инициализации при подключении с использованием ADO или IDataInitialize::GetDataSource.  
  
|Ключевое слово|Описание|Значение|  
|-------------|-----------------|-----------|  
|ServerSPN|Имя участника-службы сервера|Имя участника-службы для сервера. Значение по умолчанию — пустая строка, вследствие чего драйвер OLE DB для SQL Server по умолчанию, сформированное поставщиком имя участника-службы.|  
|FailoverPartnerSPN|Имя участника-службы партнера по обеспечению отработки отказа|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка, вследствие чего драйвер OLE DB для SQL Server по умолчанию, сформированное поставщиком имя участника-службы.|  
  
## <a name="data-source-initialization-properties"></a>Свойства инициализации источника данных  
 Следующие свойства набора свойств **DBPROPSET_SQLSERVERDBINIT** позволяют приложениям указывать имена участников-служб.  
  
|Название|Тип|Использование|  
|----------|----------|-----------|  
|SSPROP_INIT_SERVERSPN|VT_BSTR, чтение и запись|Задает имя участника-службы для сервера. Значение по умолчанию — пустая строка, вследствие чего драйвер OLE DB для SQL Server по умолчанию, сформированное поставщиком имя участника-службы.|  
|SSPROP_INIT_FAILOVERPARTNERSPN|VT_BSTR, чтение и запись|Указывает имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка, вследствие чего драйвер OLE DB для SQL Server по умолчанию, сформированное поставщиком имя участника-службы.|  
  
## <a name="data-source-properties"></a>Свойства источника данных  
 Следующие свойства набора свойств **DBPROPSET_SQLSERVERDATASOURCEINFO** позволяют приложениям распознавать метод проверки подлинности.  
  
|Название|Тип|Использование|  
|----------|----------|-----------|  
|SSPROP_INTEGRATEDAUTHENTICATIONMETHOD|VT_BSTR, только для чтения|Возвращает метод проверки подлинности, используемый для соединения. Значение, возвращаемое в приложение является значением, которое Windows возвращает драйвер OLE DB для SQL Server. Возможные следующие значения. <br />Значение «NTLM», которое возвращается в том случае, если соединение установлено с использованием проверки подлинности NTLM.<br />Значение «Kerberos», которое возвращается в том случае, если соединение установлено с использованием проверки подлинности Kerberos.<br /><br /> Если при открытом соединении нельзя определить метод проверки подлинности, то возвращается значение VT_EMPTY.<br /><br /> Это свойство доступно для чтения только в том случае, если инициализирован источник данных. При попытке считывания свойства до инициализации источника данных IDBProperties::GetProperies возвращает DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURRED, соответствующим образом и атрибута будет установлено в DBPROPSET_PROPERTIESINERROR для этого свойства. Это поведение соответствует основной спецификации OLE DB.|  
|SSPROP_MUTUALLYAUTHENICATED|VT_BOOL, только для чтения|Если при соединении серверов была выполнена взаимная проверка подлинности, возвращает значение VARIANT_TRUE. В противном случае возвращает VARIANT_FALSE.<br /><br /> Это свойство доступно для чтения только в том случае, если инициализирован источник данных. При попытке считывания свойства до инициализации источника данных IDBProperties::GetProperies возвращает DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURRED, соответствующим образом и атрибута будет установлено в DBPROPSET_ PROPERTIESINERROR для этого свойства. Это поведение соответствует основной спецификации OLE DB.<br /><br /> Если этот атрибут запрашивается соединением, не использующим проверку подлинности Windows, возвращается значение VARIANT_FALSE.|  
  
## <a name="ole-db-api-support-for-spns"></a>Поддержка OLE DB API для имен участников-служб  
 В следующей таблице описываются функции-члены OLE DB, поддерживающие имена участников-служб в клиентских соединениях.  
  
|Функция-член|Описание|  
|---------------------|-----------------|  
|IDataInitialize::GetDataSource|Параметр*pwszInitializationString* может содержать новые ключевые слова **ServerSPN** и **FailoverPartnerSPN**.|  
|IDataInitialize::GetInitializationString|Если свойства SSPROP_INIT_SERVERSPN и SSPROP_INIT_FAILOVERPARTNERSPN не имеют значений по умолчанию, они будут включены в строку инициализации с помощью параметра *ppwszInitString* в виде ключевых слов для **ServerSPN** и **FailoverPartnerSPN**. В противном случае эти ключевые слова не будут включены в строку инициализации.|  
|IDBInitialize::Initialize|Если запрос включается путем установки свойства DBPROP_INIT_PROMPT в свойствах инициализации источника данных, будет отображаться диалоговое окно входа OLE DB. Это позволяет ввести имена участников-служб как для основного сервера, так и для его партнера по обеспечению отработки отказа.<br /><br /> Строка поставщика в свойстве DPPROP_INIT_PROVIDERSTRING, если установлена, будет распознавать новые ключевые слова **ServerSPN** и **FailoverPartnerSPN** , и использовать их значения (при их наличии) для инициализации свойств SSPROP_INIT_SERVER_SPN и SSPROP_INIT_FAILOVER_PARTNER_SPN.<br /><br /> Чтобы установить свойства SSPROP_INIT_SERVER_SPN и SSPROP_INIT_FAILOVER_PARTNER_SPN до вызова IDBInitialize::Initialize может вызываться IDBProperties::SetProperties. Это является альтернативой использованию строки поставщика.<br /><br /> Если свойство устанавливается в нескольких местах, заданное программно значение имеет приоритет над значением, указанным в строке поставщика. Значение, заданное в строке инициализации, имеет приоритет над значением, заданным в диалоговом окне входа.<br /><br /> Если одно ключевое слово появляется в строке поставщика несколько раз, приоритет имеет первое значение.|  
|IDBProperties::GetProperties|IDBProperties::GetProperties можно вызвать, чтобы получить значения для нового свойства инициализации источника данных SSPROP_INIT_SERVERSPN и SSPROP_INIT_FAILOVERPARTNERSPN, а также новых свойств источника данных SSPROP_AUTHENTICATIONMETHOD и SSPROP_ MUTUALLYAUTHENTICATED.|  
|IdbProperties::GetPropertyInfo|IdbProperties::GetPropertyInfo будет включать новые свойства инициализации источника данных SSPROP_INIT_SERVERSPN и SSPROP_INIT_FAILOVERPARTNERSPN или новые свойства источника данных SSPROP_AUTHENTICATION_METHOD и SSPROP_MUTUALLYAUTHENTICATED.|  
|IDBProperties::SetProperties|IDBProperties::SetProperties может вызываться для задания свойств инициализации SSPROP_INITSERVERSPN и SSPROP_INIT_FAILOVERPARTNERSPN значения нового источника данных.<br /><br /> Эти свойства можно задать в любое время, но если источник данных уже открыт, будет возвращена следующая ошибка: DB_E_ERRORSOCCURRED, «Многошаговая операция OLE DB сформировала ошибки. Проверьте каждое значение состояния OLE DB (если возможно). Работа не была выполнена».|  
  
## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для SQL Server &#40;OLE DB&#41;](../../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)  
  
  
