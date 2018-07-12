---
title: Свойства (OLE DB) источника данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 6e14fefc-4e0b-4847-a833-4cf0abe65d50
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f108559bebad1ab98fc0c81ce0492293a9632e5b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419336"
---
# <a name="data-source-properties-ole-db"></a>Свойства источника данных (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента реализует свойства источника данных следующим образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_CURRENTCATALOG|Чтение и запись и запись: по умолчанию: нет<br /><br /> Описание: Значение dbprop_currentcatalog указывает сообщает текущую базу данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сеанс поставщика OLE DB для собственного клиента. Установка значения свойства действует идентичны, как установка текущей базы данных с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] используйте *базы данных* инструкции.<br /><br /> Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], при вызове [sp_defaultdb](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md) и укажите имя базы данных в нижний регистр, даже если она была изначально создана с именем в смешанном регистре, DBPROP_CURRENTCATALOG возвратит имя в нижнем регистре. В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] свойство DBPROP_CURRENTCATALOG возвращало имя в ожидаемом смешанном регистре.|  
|DBPROP_MULTIPLECONNECTIONS|По умолчанию и запись: чтение и запись: VARIANT_FALSE<br /><br /> Описание: Если подключение выполняется команда, не производящей набор строк или производящей набор строк, который не является серверным курсором, и одновременно выполняется другая команда, новое соединение будет создаваться для выполнения этой команды в том случае, если свойство DBPROP_MULTIPLECONNECTIONS имеет VARIANT_ ЗНАЧЕНИЕ TRUE.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента не создает другого соединения, если свойство DBPROP_MULTIPLECONNECTION имеет значение VARIANT_FALSE или если транзакция является активной в соединении. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает значение DB_E_OBJECTOPEN, если свойство DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_FALSE и возвращает E_FAIL, если активная транзакция. Управление транзакциями и блокировками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] производит отдельно для каждого соединения. Если создано второе соединение, команды в отдельных соединениях не используют общие блокировки. Чтобы убедиться, что одна команда не блокирует другую, удерживайте блокировки строк, запрошенных другой командой. Это верно и при создании нескольких сеансов.<br /><br /> Каждый сеанс имеет отдельное соединение.|  
  
 В от поставщика наборе свойств DBPROPSET_SQLSERVERDATASOURCE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента определяет следующие дополнительные свойства источника данных.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_ENABLEFASTLOAD|По умолчанию и запись: чтение и запись: VARIANT_FALSE<br /><br /> Описание: Чтобы включить массовое копирование из памяти, свойство SSPROP_ENABLEFASTLOAD должно быть присвоить значение VARIANT_TRUE. Это свойство установлено в источнике данных, вновь созданный сеанс позволяет потребителю получить доступ к [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) интерфейс.<br /><br /> Если свойство имеет значение VARIANT_TRUE, **IRowsetFastLoad** интерфейс доступен через **IOpenRowset::OpenRowset** , запрашивая **IID_IRowsetFastLoad** интерфейс, либо задав **SSPROP_IRowsetFastLoad** значение VARIANT_TRUE.|  
|SSPROP_ENABLEBULKCOPY|По умолчанию и запись: чтение и запись: VARIANT_FALSE<br /><br /> Описание: Чтобы включить массовое копирование из файлов, свойству SSPROP_ENABLEBULKCOPY должно быть присвоено значение VARIANT_TRUE. Если это свойство установлено в источнике данных, потребитель получает доступ к интерфейсу IBCPSession с тем же уровнем, что и сеанс.<br /><br /> Свойство SSPROP_IRowsetFastLoad также должно быть установлено в значение VARIANT_TRUE.|  
  
## <a name="see-also"></a>См. также  
 [Объекты источника данных &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
