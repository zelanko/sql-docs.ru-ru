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
ms.openlocfilehash: 7915b9fb74f05057e05eef022d7f9b0e4ccdd21f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989255"
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>Обновление приложения с переходом от собственного клиента SQL Server 2005
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В этом разделе обсуждаются критические изменения в драйвере OLE DB для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQL Server, начиная [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]с собственного клиента в.  

 При обновлении с компонентов доступа к данным MDAC до драйвера OLE DB для SQL Server могут возникнуть определенные изменения в работе. Дополнительные сведения см. [в разделе Обновление приложения до OLE DB драйвера для SQL Server из MDAC](../../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  

 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 поставляется в составе [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 поставляется в составе [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 10.5 поставляется в составе [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]. Клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 поставляется в составе [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] и [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].  

|Измененное поведение в драйвере OLE DB для SQL Server [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] по сравнению с собственным клиентом|Описание|  
|------------------------------------------------------------------------------------|-----------------|  
|OLE DB дополняет данные только до заданного масштаба.|Для преобразований, в которых преобразованные данные отправляются на сервер, OLE DB драйвер для SQL Server в качестве конечных нулей в данных до максимальной длины значений **DateTime** . Собственный клиент SQL Server версии 9.0 дополнял данные до 9 разрядов.|  
|Проверьте DBTYPE_DBTIMESTAMP для Икоммандвиспараметер:: SetParameterInfo.|Драйвер OLE DB для SQL Server реализует требование OLE DB для *bScale* в икоммандвиспараметер:: SetParameterInfo для установки значения точности доли секунды для DBTYPE_DBTIMESTAMP.|  
|Хранимая процедура **sp_columns** теперь возвращает значение **"No"** вместо **"No"** для столбца IS_NULLABLE.|В драйвере OLE DB для SQL Server хранимая процедура **sp_columns** теперь возвращает **"No** " вместо **"No"** для столбца IS_NULLABLE.|  
|При выходе значения даты за пределы диапазона теперь происходит возврат другого значения ошибки.|Для типа **DateTime** в драйвере OLE DB будет возвращен другой номер ошибки для SQL Server, если дата выходит за пределы диапазона, чем было возвращено в предыдущих версиях.<br /><br /> В частности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , собственный клиент 9,0 вернул 22007 для всех диапазонов значений года при преобразовании строк в **DateTime**, а OLE DB драйвер для SQL Server возвращает 22008, если дата находится в диапазоне, поддерживаемом **datetime2** , но снаружи. диапазон, поддерживаемый **DateTime** или **smalldatetime**.|  
|В значении **datetime** усекаются доли секунды, а округление не происходит, если при округлении изменится значение дня.|До появления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 клиент, передавая данные типа **datetime** на сервер, округлял их до ближайшей 1/300-й доли секунды. В OLE DB драйвере для SQL Server этот сценарий приводит к усечению доли секунды, если изменение округления выполняется в день.|  
|Возможные усечение в секундах для значения **DateTime** .|В приложении, созданном с помощью драйвера OLE DB для SQL Server, при подключении к серверу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2005 будут усекаться секунды и доли секунды в части отправленных на сервер данных, относящейся ко времени, если выполняется привязка к столбцу типа datetime с идентификатором типа DBTYPE_DBTIMESTAMP (OLE DB) или SQL_TIMESTAMP (ODBC) и масштабом 0.<br /><br /> Пример:<br /><br /> Входные данные: 1994-08-21 21:21:36.000<br /><br /> Вставляемые данные: 1994-08-21 21:21:00.000|  
|Преобразование данных OLE DB из типа DBTYPE_DBTIME в DBTYPE_DATE больше не вызывает изменения значения дня.|До появления собственного клиента версии 10.0 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], если часть времени для значения DBTYPE_DATE отстояла от полуночи не более чем на полсекунды, то применение кода преобразования OLE DB приводило к изменению дня. В драйвере OLE DB для SQL Server день не изменится (доли секунды усекаются и не округляются).|  
|Изменения преобразования IBCPSession::BCColFmt.|В драйвере OLE DB для SQL Server при использовании IBCPSession:: Бкоколфмт для преобразования SQLDATETIME или SQLDATETIME в строковый тип экспортируется дробное значение. Например, при преобразовании типа SQLDATETIME в тип SQLNVARCHARMAX версии до [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 возвращали следующее:<br /> 1989-02-01 00:00:00.<br />Драйвер OLE DB для SQL Server возвращает следующее: <br />1989-02-01 00:00:00.0000000.|  
|В пользовательских приложениях, в которых используется API BCP, теперь могут обнаруживаться предупреждающие сообщения.|API BCP выдает предупреждающее сообщение, если длина данных превышает заданную длину для полей всех типов. Раньше это предупреждение выдавалось только для символьных типов, но не для всех типов.|  
|Вставка пустой строки в объект типа **sql_variant**, привязанный как тип даты и времени, вызывает ошибку.|В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 вставка пустой строки в объект типа **sql_variant**, привязанный как тип даты и времени, не вызывала ошибки. Драйвер OLE DB для SQL Server правильно выдает ошибку в этой ситуации.|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может возвращать различные результаты при выполнении триггера.|Изменения, внесенные в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], могут привести к тому, что приложение получит другие результаты при выполнении инструкции, вызвавшей выполнение триггера при действующем параметре **NOCOUNT OFF**. В такой ситуации в приложении может возникнуть ошибка. Чтобы устранить эту ошибку, установите параметр **NOCOUNT ON** в триггере.|  

## <a name="see-also"></a>См. также:   
 [Драйвер OLE DB для SQL Server](../../oledb/oledb-driver-for-sql-server.md)
