---
title: Обновление приложения от собственного клиента SQL Server 2005 | Документы Microsoft
description: Обновление приложения от собственного клиента SQL Server 2005
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, updating applications
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: faea11704538aea426d5c1c6fdbe8018893dcdc4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>Обновление приложения с переходом от собственного клиента SQL Server 2005
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В этом разделе рассматриваются критические изменения в драйвер OLE DB для SQL Server с момента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  

 При обновлении из Microsoft данных Access Components (MDAC) драйвер OLE DB для SQL Server, также возможны некоторые различия в поведении. Дополнительные сведения см. в разделе [обновление приложения для драйвера OLE DB для SQL Server с компонентами MDAC](../../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  

 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственный клиент версии 9.0, поставляемых с [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственный клиент версии 10.0, поставляемых с [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 10.5 поставляется в составе [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]. Клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 поставляется в составе [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] и [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].  

|Изменить поведение драйвера OLE DB для SQL Server, по сравнению с [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client|Описание|  
|------------------------------------------------------------------------------------|-----------------|  
|OLE DB дополняет данные только до заданного масштаба.|Для выполнения преобразований, где преобразованные данные передаются на сервер, драйвер OLE DB для SQL Server дополняет конечные нули в данных только до максимальной длины **datetime** значения. Собственный клиент SQL Server версии 9.0 дополнял данные до 9 разрядов.|  
|Проверьте ICommandWithParameter::SetParameterInfo DBTYPE_DBTIMESTAMP.|Драйвер OLE DB для SQL Server реализует требование OLE DB для *bScale* в ICommandWithParameter::SetParameterInfo будет присвоено точность в долях секунды для структуры DBTYPE_DBTIMESTAMP.|  
|**Sp_columns** хранимая процедура возвращает сейчас **«NO»** вместо **«NO»** применительно к столбцу is_nullable.|В драйвер OLE DB для SQL Server **sp_columns** хранимая процедура возвращает сейчас **«NO»** вместо **«NO»** для к столбцу is_nullable.|  
|При выходе значения даты за пределы диапазона теперь происходит возврат другого значения ошибки.|Для **datetime** , другой номер ошибки возвращается тип драйвером OLE DB для SQL Server при обнаружении даты вне диапазона не был возвращен в более ранних версиях.<br /><br /> В частности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент версии 9.0 возвращается 22007 для всех выходящих за пределы диапазона значений года при преобразовании строки в **datetime**, и драйвер OLE DB для SQL Server возвращает 22008, если дата находится в пределах диапазона, поддерживаемого **datetime2** , но за пределами диапазона, поддерживаемого **datetime** или **smalldatetime**.|  
|**DateTime** значение усекаются доли секунды, а не round if округлении изменится значение дня.|До появления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, поведение клиента для **datetime** значения, отправляемых на сервер — округлял их до ближайшей 1/300 секунды. В драйвер OLE DB для SQL Server этот сценарий вызывает усечение долей секунды, если округление изменяет дня.|  
|Возможно усечение секунд для **datetime** значение.|Приложения, созданного с помощью драйвера OLE DB для SQL Server, который подключается к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2005 server будут усекаться секунды и долей секунды для временной части данных, отправляемых на сервер, если выполняется привязка к столбцу типа datetime с идентификатором типа DBTYPE_DBTIMESTAMP () OLE DB) или SQL_TIMESTAMP (ODBC) и масштабом 0.<br /><br /> Например:<br /><br /> Входные данные: 21:21:36.000 1994-08-21<br /><br /> Данные вставлены: 21:21:00.000 1994-08-21|  
|Преобразование данных OLE DB из типа DBTYPE_DBTIME в DBTYPE_DATE больше не вызывает изменения значения дня.|До появления собственного клиента версии 10.0 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], если часть времени для значения DBTYPE_DATE отстояла от полуночи не более чем на полсекунды, то применение кода преобразования OLE DB приводило к изменению дня. В драйвер OLE DB для SQL Server, будет день не изменяется (доли секунды усекается и не округляется).|  
|Изменения IBCPSession::BCColFmt преобразования.|При использовании IBCPSession::BCOColFmt для преобразования типа SQLDATETIME или SQLDATETIME в строковый тип в драйвер OLE DB для SQL Server, экспортируется дробные значения. Например, при преобразовании типа SQLDATETIME в тип SQLNVARCHARMAX версии, предшествующие [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращается Native Client 10.0<br /> 1989-02-01 00:00:00.<br />Драйвер OLE DB для SQL Server возвращает <br />00:00:00.0000000 1989-02-01.|  
|В пользовательских приложениях, в которых используется API BCP, теперь могут обнаруживаться предупреждающие сообщения.|API BCP выдает предупреждающее сообщение, если длина данных превышает заданную длину для полей всех типов. Раньше это предупреждение выдавалось только для символьных типов, но не для всех типов.|  
|Вставка пустой строки в **sql_variant** привязанный как тип даты и времени выдает ошибку.|В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент версии 9.0, Вставка пустой строки в **sql_variant** привязанный как тип даты и времени не привел к созданию ошибку. Драйвер OLE DB для SQL Server правильно приводит к возникновению ошибки в этой ситуации.|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может возвращать различные результаты при выполнении триггера.|Изменения, появившиеся в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] может привести к приложению с различными результатами, возвращаемых инструкцией, вызвавшей выполнение триггера при **NOCOUNT OFF** была действующей. В такой ситуации в приложении может возникнуть ошибка. Чтобы устранить эту ошибку, установите **NOCOUNT ON** в триггере.|  

## <a name="see-also"></a>См. также   
 [Драйвер OLE DB для SQL Server](../../oledb/oledb-driver-for-sql-server.md)
