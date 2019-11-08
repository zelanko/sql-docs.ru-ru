---
title: Свойства источника данных (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 6e14fefc-4e0b-4847-a833-4cf0abe65d50
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 50a5f3ba0a306f2c170e62965b84074592387c25
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73774681"
---
# <a name="data-source-properties-ole-db"></a>Свойства источника данных (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB реализует свойства источника данных следующим образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_CURRENTCATALOG|R/W: чтение/запись по умолчанию: нет<br /><br /> Описание: значение DBPROP_CURRENTCATALOG сообщает о текущей базе данных о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сеансе поставщика собственного клиента OLE DB. Установка значения этого свойства равноценна установке текущей базы данных с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] USE *база_данных*.<br /><br /> Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] при вызове хранимой процедуры [sp_defaultdb](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md) и указании имени базы данных в нижнем регистре, даже если база данных первоначально была создана с именем в смешанном регистре, свойство DBPROP_CURRENTCATALOG возвратит имя в нижнем регистре. В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] свойство DBPROP_CURRENTCATALOG возвращало имя в ожидаемом смешанном регистре.|  
|DBPROP_MULTIPLECONNECTIONS|R/W: чтение и запись по умолчанию: VARIANT_FALSE<br /><br /> Описание: если в рамках подключения выполняется команда, не создающая набор строк или создающая набор строк, который не является серверным курсором, и одновременно выполняется другая команда, для выполнения этой команды создается новое подключение, если свойство DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_TRUE.<br /><br /> Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB не будет создавать другое соединение, если DBPROP_MULTIPLECONNECTION VARIANT_FALSE или если транзакция активна в соединении. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает DB_E_OBJECTOPEN, если DBPROP_MULTIPLECONNECTIONS VARIANT_FALSE, и возвращает E_FAIL при наличии активной транзакции. Управление транзакциями и блокировками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] производит отдельно для каждого соединения. Если создано второе соединение, команды в отдельных соединениях не используют общие блокировки. Чтобы убедиться, что одна команда не блокирует другую, удерживайте блокировки строк, запрошенных другой командой. Это верно и при создании нескольких сеансов.<br /><br /> Каждый сеанс имеет отдельное соединение.|  
  
 В DBPROPSET_SQLSERVERDATASOURCE свойств, зависящих от поставщика, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB Native Client определяет следующие дополнительные свойства источника данных.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_ENABLEFASTLOAD|R/W: чтение и запись по умолчанию: VARIANT_FALSE<br /><br /> Описание: чтобы включить массовое копирование из памяти, свойству SSPROP_ENABLEFASTLOAD необходимо присвоить значение VARIANT_TRUE. Если это свойство установлено в источнике данных, вновь созданный сеанс позволяет потребителю получить доступ к интерфейсу [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md).<br /><br /> Если это свойство имеет значение VARIANT_TRUE, доступ к интерфейсу **IRowsetFastLoad** можно получить через метод **IOpenRowset::OpenRowset**, запросив интерфейс **IID_IRowsetFastLoad**, или с помощью присвоения свойству **SSPROP_IRowsetFastLoad** значения VARIANT_TRUE.|  
|SSPROP_ENABLEBULKCOPY|R/W: чтение и запись по умолчанию: VARIANT_FALSE<br /><br /> Описание: чтобы включить массовое копирование из файлов, свойству SSPROP_ENABLEBULKCOPY необходимо присвоить значение VARIANT_TRUE. Если это свойство установлено в источнике данных, потребитель получает доступ к интерфейсу IBCPSession с тем же уровнем, что и сеанс.<br /><br /> Свойство SSPROP_IRowsetFastLoad также должно быть установлено в значение VARIANT_TRUE.|  
  
## <a name="see-also"></a>См. также раздел  
 [Объекты &#40;источника данных OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
