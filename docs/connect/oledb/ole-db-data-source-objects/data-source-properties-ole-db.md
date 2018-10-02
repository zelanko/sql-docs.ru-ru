---
title: Свойства (OLE DB) источника данных | Документация Майкрософт
description: Свойства источника данных (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- OLE DB data source properties [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: a42b585dd32926d018839b3a71db74424ca23bef
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47785532"
---
# <a name="data-source-properties-ole-db"></a>Свойства источника данных (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server реализует свойства источника данных следующим образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_CURRENTCATALOG|Чтение и запись и запись: по умолчанию: нет<br /><br /> Описание: Значение dbprop_currentcatalog указывает сообщает текущей базы данных для драйвера OLE DB для SQL Server сеанса. Установка значения этого свойства равноценна установке текущей базы данных с помощью инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] USE *база_данных*.<br /><br /> Начиная с версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] при вызове хранимой процедуры [sp_defaultdb](../../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md) и указании имени базы данных в нижнем регистре, даже если база данных первоначально была создана с именем в смешанном регистре, свойство DBPROP_CURRENTCATALOG возвратит имя в нижнем регистре. В предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] свойство DBPROP_CURRENTCATALOG возвращало имя в ожидаемом смешанном регистре.|  
|DBPROP_MULTIPLECONNECTIONS|По умолчанию и запись: чтение и запись: VARIANT_FALSE<br /><br /> Описание: если в рамках подключения выполняется команда, не создающая набор строк или создающая набор строк, который не является серверным курсором, и одновременно выполняется другая команда, для выполнения этой команды создается новое подключение, если свойство DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_TRUE.<br /><br /> Драйвер OLE DB для SQL Server не создает другое подключение, если свойство DBPROP_MULTIPLECONNECTION имеет значение VARIANT_FALSE или если в подключении имеется активная транзакция. Драйвер OLE DB для SQL Server возвращает значение DB_E_OBJECTOPEN, если свойство DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_FALSE, и значение E_FAIL, если существует активная транзакция. Управление транзакциями и блокировками [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] производит отдельно для каждого соединения. Если создано второе соединение, команды в отдельных соединениях не используют общие блокировки. Чтобы убедиться, что одна команда не блокирует другую, удерживайте блокировки строк, запрошенных другой командой. Это верно и при создании нескольких сеансов.<br /><br /> Каждый сеанс имеет отдельное соединение.|  
  
 В зависящем от поставщика наборе свойств DBPROPSET_SQLSERVERDATASOURCE драйвер OLE DB для SQL Server определяет указанные ниже дополнительные свойства источника данных.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_ENABLEFASTLOAD|По умолчанию и запись: чтение и запись: VARIANT_FALSE<br /><br /> Описание: чтобы включить массовое копирование из памяти, свойству SSPROP_ENABLEFASTLOAD необходимо присвоить значение VARIANT_TRUE. Если это свойство установлено в источнике данных, вновь созданный сеанс позволяет потребителю получить доступ к интерфейсу [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md).<br /><br /> Если это свойство имеет значение VARIANT_TRUE, доступ к интерфейсу **IRowsetFastLoad** можно получить через метод **IOpenRowset::OpenRowset**, запросив интерфейс **IID_IRowsetFastLoad**, или с помощью присвоения свойству **SSPROP_IRowsetFastLoad** значения VARIANT_TRUE.|  
|SSPROP_ENABLEBULKCOPY|По умолчанию и запись: чтение и запись: VARIANT_FALSE<br /><br /> Описание: чтобы включить массовое копирование из файлов, свойству SSPROP_ENABLEBULKCOPY необходимо присвоить значение VARIANT_TRUE. Если это свойство установлено в источнике данных, потребитель получает доступ к интерфейсу IBCPSession с тем же уровнем, что и сеанс.<br /><br /> Свойство SSPROP_IRowsetFastLoad также должно быть установлено в значение VARIANT_TRUE.|  
  
## <a name="see-also"></a>См. также:  
 [Объекты источника данных &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
