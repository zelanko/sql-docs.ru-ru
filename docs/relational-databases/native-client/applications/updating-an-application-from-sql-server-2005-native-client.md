---
title: Обновление приложения от собственного клиента SQL Server 2005 | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, updating applications
ms.assetid: 1e1e570c-7f14-4e16-beab-c328e3fbdaa8
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a2181b027627e89b14c774185fa15a8cec2c3444
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>Обновление приложения с переходом от собственного клиента SQL Server 2005
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  В этом разделе рассматриваются критические изменения в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в сравнении с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 При обновлении с компонентов доступа к данным MDAC к собственному клиенту [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] могут возникнуть определенные изменения в работе. Дополнительные сведения см. в разделе [обновление приложения для собственного клиента SQL Server с компонентами MDAC](../../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственный клиент версии 9.0, поставляемых с [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственный клиент версии 10.0, поставляемых с [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 10.5 поставляется в составе [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]. Клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 поставляется в составе [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] и [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].  
  
|Изменения в поведении собственного клиента SQL Server, начиная с версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]|Описание|  
|------------------------------------------------------------------------------------|-----------------|  
|OLE DB дополняет данные только до заданного масштаба.|Для выполнения преобразований, где преобразованные данные передаются на сервер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (начиная с версии [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) дополняет данные только до максимальной длины завершающими нулями **datetime** значения. Собственный клиент SQL Server версии 9.0 дополнял данные до 9 разрядов.|  
|Проверьте ICommandWithParameter::SetParameterInfo DBTYPE_DBTIMESTAMP.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (начиная с версии [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) реализуется требование OLE DB для *bScale* в ICommandWithParameter::SetParameterInfo будет присвоено точность в долях секунды для структуры DBTYPE_DBTIMESTAMP.|  
|**Sp_columns** хранимая процедура возвращает сейчас **«NO»** вместо **«NO»** применительно к столбцу is_nullable.|Начиная с версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент версии 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]), **sp_columns** хранимая процедура возвращает сейчас **«NO»** вместо **«NO»** для к столбцу is_nullable .|  
|SQLSetDescRec, SQLBindCol и SQLBindParameter теперь обеспечивают проверку согласованности.|До появления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент версии 10.0, параметр SQL_DESC_DATA_PTR не приводит к проверку согласованности для любого типа дескриптора в SQLSetDescRec, SQLBindCol и SQLBindParameter.|  
|SQLCopyDesc теперь проверяет согласованность дескрипторов.|До появления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент версии 10.0, SQLCopyDesc не проверку согласованности при для конкретной записи был задан параметр sql_desc_data_ptr.|  
|SQLGetDescRec больше не проверяет согласованность дескрипторов.|До появления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент версии 10.0, SQLGetDescRec выполнить проверку согласованности, если был задан параметр sql_desc_data_ptr. Этого не требовалось по спецификации ODBC, и собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) и более поздних версий уже не проводит эту проверку согласованности.|  
|При выходе значения даты за пределы диапазона теперь происходит возврат другого значения ошибки.|Для **datetime** типа, другой номер ошибки будут возвращаться [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента (начиная с версии [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) для вне диапазона дат не был возвращен в более ранних версиях.<br /><br /> В частности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент версии 9.0 возвращается 22007 для всех выходящих за пределы диапазона значений года при преобразовании строки в **datetime**, и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, начиная с версии 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) возвращает 22008 Если Дата находится в пределах диапазона, поддерживаемого **datetime2** , но за пределами диапазона, поддерживаемого **datetime** или **smalldatetime**.|  
|**DateTime** значение усекаются доли секунды, а не round if округлении изменится значение дня.|До появления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, поведение клиента для **datetime** значения, отправляемых на сервер — округлял их до ближайшей 1/300 секунды. Начиная с собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии 10.0, в этой ситуации происходит усечение долей секунды, если округление приводит к изменению значения дня.|  
|Возможно усечение секунд для **datetime** значение.|В приложении, построенном с помощью собственного клиента [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (или более поздних версий), при подключении к серверу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2005 (или более ранней версии) будут усекаться секунды и доли секунды в части отправленных на сервер данных, относящейся ко времени, если выполняется привязка к столбцу типа datetime с идентификатором типа DBTYPE_DBTIMESTAMP (OLE DB) или SQL_TIMESTAMP (ODBC) и масштабом 0.<br /><br /> Например:<br /><br /> Входные данные: 21:21:36.000 1994-08-21<br /><br /> Данные вставлены: 21:21:00.000 1994-08-21|  
|Преобразование данных OLE DB из типа DBTYPE_DBTIME в DBTYPE_DATE больше не вызывает изменения значения дня.|До появления собственного клиента версии 10.0 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], если часть времени для значения DBTYPE_DATE отстояла от полуночи не более чем на полсекунды, то применение кода преобразования OLE DB приводило к изменению дня. Начиная с собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии 10.0, день не изменяется (доли секунды усекаются, а не округляются).|  
|Изменения IBCPSession::BCColFmt преобразования.|Начиная с версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экспортируется собственный клиент версии 10.0, при использовании IBCPSession::BCOColFmt для преобразования типа SQLDATETIME или SQLDATETIME в строковый тип, а дробные значения. Например, при преобразовании типа SQLDATETIME в тип SQLNVARCHARMAX более ранние версии собственного клиента для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращали следующее:<br /><br /> 1989-02-01 00:00:00. Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии 10.0 и более поздних версий возвращает 1989-02-01 00:00:00.0000000.|  
|Размер пересылаемых данных должен соответствовать длине, заданной параметром SQL_LEN_DATA_AT_EXEC.|При использовании параметра SQL_LEN_DATA_AT_EXEC размер данных должен соответствовать длине, заданной параметром SQL_LEN_DATA_AT_EXEC. Можно использовать параметр SQL_DATA_AT_EXEC, но SQL_LEN_DATA_AT_EXEC дает некоторый выигрыш в производительности.|  
|В пользовательских приложениях, в которых используется API BCP, теперь могут обнаруживаться предупреждающие сообщения.|API BCP выдает предупреждающее сообщение, если длина данных превышает заданную длину для полей всех типов. Раньше это предупреждение выдавалось только для символьных типов, но не для всех типов.|  
|Вставка пустой строки в **sql_variant** привязанный как тип даты и времени выдает ошибку.|В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент версии 9.0, Вставка пустой строки в **sql_variant** привязанный как тип даты и времени не привел к созданию ошибку. Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии 10.0 (или более поздних версий) в этом случае совершенно обоснованно возвращает ошибку.|  
|Более строгая проверка параметров типа SQL_C_TYPE _TIMESTAMP и DBTYPE_DBTIMESTAMP.|До появления [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client **datetime** происходило округление значений для соответствия масштабу **datetime** и **smalldatetime** по столбцу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Теперь в собственном клиенте [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (и более поздних версиях) применяются более строгие правила проверки, определенные в базовой спецификации ODBC для долей секунды. Если значение параметра не удается преобразовать в тип SQL с помощью масштаба, заданного или подразумеваемого клиентской привязкой, без усечения конечных разрядов, то возвращается ошибка.|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может возвращать различные результаты при выполнении триггера.|Изменения, появившиеся в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] может привести к приложению с различными результатами, возвращаемых инструкцией, вызвавшей выполнение триггера при **NOCOUNT OFF** была действующей. В такой ситуации в приложении может возникнуть ошибка. Чтобы устранить эту ошибку, установите **NOCOUNT ON** в триггер или вызов SQLMoreResults, чтобы перейти к следующему результату.|  
  
## <a name="see-also"></a>См. также  
 [Программирование собственного клиента SQL Server](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
