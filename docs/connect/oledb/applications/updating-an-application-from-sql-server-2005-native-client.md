---
title: Обновление приложения с переходом от SQL Server 2005 Native Client | Документы Майкрософт
description: Обновление приложения с переходом от SQL Server 2005 Native Client
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, updating applications
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 17280079f493d8abbad2f8ffb76d25c2a0ba868f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66771065"
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>Обновление приложения с переходом от собственного клиента SQL Server 2005
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В этом разделе рассматриваются критические изменения в драйвере OLE DB для SQL Server с момента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  

 При обновлении с компонентов доступа к данным MDAC до драйвера OLE DB для SQL Server могут возникнуть определенные изменения в работе. Дополнительные сведения см. в разделе [обновление приложения для драйвера OLE DB для SQL Server с компонентами MDAC](../../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  

 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 поставляется в составе [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 поставляется в составе [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 10.5 поставляется в составе [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]. Клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 поставляется в составе [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] и [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].  

|Изменено поведение в драйвере OLE DB для SQL Server, по сравнению с [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client|Описание|  
|------------------------------------------------------------------------------------|-----------------|  
|OLE DB дополняет данные только до заданного масштаба.|Для выполнения преобразований, где преобразованные данные передаются на сервер, драйвер OLE DB для SQL Server дополняет данные только до максимальной длины из завершающими нулями **datetime** значения. Собственный клиент SQL Server версии 9.0 дополнял данные до 9 разрядов.|  
|Проверьте ICommandWithParameter::SetParameterInfo DBTYPE_DBTIMESTAMP.|Драйвер OLE DB для SQL Server реализует требование OLE DB для *bScale* в ICommandWithParameter::SetParameterInfo будет присвоено точность в долях секунды для структуры DBTYPE_DBTIMESTAMP.|  
|**Sp_columns** хранимая процедура возвращает теперь **«Нет»** вместо **«Нет»** применительно к столбцу IS_NULLABLE.|В драйвер OLE DB для SQL Server **sp_columns** хранимая процедура возвращает теперь **«Нет»** вместо **«Нет»** применительно к столбцу IS_NULLABLE.|  
|При выходе значения даты за пределы диапазона теперь происходит возврат другого значения ошибки.|Для **datetime** , другой номер ошибки возвращается тип драйвером OLE DB для SQL Server ошибку вне диапазона даты не был возвращен в более ранних версий.<br /><br /> В частности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент версии 9.0 возвращаемых 22007 для всех выходящих за пределы диапазона значений года при преобразовании строки в тип **datetime**, и драйвер OLE DB для SQL Server возвращает 22008, если дата попадает в диапазон, поддерживаемый **datetime2** , но за пределами диапазона, поддерживаемого **datetime** или **smalldatetime**.|  
|В значении **datetime** усекаются доли секунды, а округление не происходит, если при округлении изменится значение дня.|До появления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 клиент, передавая данные типа **datetime** на сервер, округлял их до ближайшей 1/300-й доли секунды. В драйвер OLE DB для SQL Server при таком сценарии происходит усечение долей секунды, если округление к изменению значения дня.|  
|Возможно усечение секунд для **datetime** значение.|В приложении, созданном с помощью драйвера OLE DB для SQL Server, при подключении к серверу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2005 будут усекаться секунды и доли секунды в части отправленных на сервер данных, относящейся ко времени, если выполняется привязка к столбцу типа datetime с идентификатором типа DBTYPE_DBTIMESTAMP (OLE DB) или SQL_TIMESTAMP (ODBC) и масштабом 0.<br /><br /> Пример:<br /><br /> Входные данные: 1994-08-21 21:21:36.000<br /><br /> Вставляемые данные: 1994-08-21 21:21:00.000|  
|Преобразование данных OLE DB из типа DBTYPE_DBTIME в DBTYPE_DATE больше не вызывает изменения значения дня.|До появления собственного клиента версии 10.0 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], если часть времени для значения DBTYPE_DATE отстояла от полуночи не более чем на полсекунды, то применение кода преобразования OLE DB приводило к изменению дня. В драйвер OLE DB для SQL Server, будет день не изменяется (доли секунды усекаются и не округляются).|  
|Изменения преобразования IBCPSession::BCColFmt.|В драйвер OLE DB для SQL Server при использовании IBCPSession::BCOColFmt для преобразования типа SQLDATETIME или SQLDATETIME в строковый тип происходит экспорт дробной. Например, при преобразовании типа SQLDATETIME в тип SQLNVARCHARMAX версии до [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 возвращали следующее:<br /> 1989-02-01 00:00:00.<br />Драйвер OLE DB для SQL Server возвращает следующее: <br />1989-02-01 00:00:00.0000000.|  
|В пользовательских приложениях, в которых используется API BCP, теперь могут обнаруживаться предупреждающие сообщения.|API BCP выдает предупреждающее сообщение, если длина данных превышает заданную длину для полей всех типов. Раньше это предупреждение выдавалось только для символьных типов, но не для всех типов.|  
|Вставка пустой строки в объект типа **sql_variant**, привязанный как тип даты и времени, вызывает ошибку.|В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 вставка пустой строки в объект типа **sql_variant**, привязанный как тип даты и времени, не вызывала ошибки. В этом случае драйвер OLE DB для SQL Server правильно возвращает ошибку.|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может возвращать различные результаты при выполнении триггера.|Изменения, внесенные в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], могут привести к тому, что приложение получит другие результаты при выполнении инструкции, вызвавшей выполнение триггера при действующем параметре **NOCOUNT OFF**. В такой ситуации в приложении может возникнуть ошибка. Чтобы устранить эту ошибку, задайте **NOCOUNT ON** в триггере.|  

## <a name="see-also"></a>См. также:   
 [Драйвер OLE DB для SQL Server](../../oledb/oledb-driver-for-sql-server.md)
