---
title: Свойства (OLE DB) источника данных | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: a693d424528819c71663e8be9dd580782eebb637
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694905"
---
# <a name="data-source-properties-ole-db"></a>Свойства источника данных (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента реализует свойства источника данных следующим образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_CURRENTCATALOG|R Чтение и запись: чтение и запись по умолчанию: нет<br /><br /> Описание: Значение DBPROP_CURRENTCATALOG сообщает текущую базу данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сеанс поставщика OLE DB для собственного клиента. Задание значения свойства действует идентичные как задание текущей базы данных с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] используйте *базы данных* инструкции.<br /><br /> Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], при вызове [sp_defaultdb](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md) и укажите имя базы данных в нижнем регистре, даже если база данных была создана с именем в смешанном регистре, свойство DBPROP_CURRENTCATALOG возвратит имя в нижнем регистре. В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] свойство DBPROP_CURRENTCATALOG возвращало имя в ожидаемом смешанном регистре.|  
|DBPROP_MULTIPLECONNECTIONS|По умолчанию R Чтение и запись: чтение и запись: VARIANT_FALSE<br /><br /> Описание: Если соединение выполняется команда, производящей набор строк или производящей набор строк, не являющегося серверный курсор, выполняется другая команда новое соединение будет создаваться для выполнения этой команды, если свойство DBPROP_MULTIPLECONNECTIONS имеет VARIANT_ ЗНАЧЕНИЕ TRUE.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента не будет создать другое подключение, если свойство DBPROP_MULTIPLECONNECTION имеет значение VARIANT_FALSE или если транзакция активна в соединении. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает значение DB_E_OBJECTOPEN, если свойство DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_FALSE и вернет значение E_FAIL, если нет активной транзакции. Управление транзакциями и блокировками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] производит отдельно для каждого соединения. Если создано второе соединение, команды в отдельных соединениях не используют общие блокировки. Чтобы убедиться, что одна команда не блокирует другую, удерживайте блокировки строк, запрошенных другой командой. Это верно и при создании нескольких сеансов.<br /><br /> Каждый сеанс имеет отдельное соединение.|  
  
 В специфический для поставщика наборе свойств DBPROPSET_SQLSERVERDATASOURCE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента определяет следующие дополнительные свойства источника данных.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_ENABLEFASTLOAD|По умолчанию R Чтение и запись: чтение и запись: VARIANT_FALSE<br /><br /> Описание: Чтобы включить массовое копирование из памяти, свойство SSPROP_ENABLEFASTLOAD задавайте значение VARIANT_TRUE. Это свойство установлено в источнике данных, вновь созданный сеанс позволяет потребителю получить доступ к [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) интерфейса.<br /><br /> Если свойство имеет значение VARIANT_TRUE, **IRowsetFastLoad** интерфейс доступен через **IOpenRowset::OpenRowset** , запрашивая **IID_IRowsetFastLoad** интерфейс или путем установки **SSPROP_IRowsetFastLoad** значение VARIANT_TRUE.|  
|SSPROP_ENABLEBULKCOPY|По умолчанию R Чтение и запись: чтение и запись: VARIANT_FALSE<br /><br /> Описание: Чтобы включить массовое копирование из файлов, свойству SSPROP_ENABLEBULKCOPY должно быть присвоено значение VARIANT_TRUE. Если это свойство установлено в источнике данных, потребитель получает доступ к интерфейсу IBCPSession с тем же уровнем, что и сеанс.<br /><br /> Свойство SSPROP_IRowsetFastLoad также должно быть установлено в значение VARIANT_TRUE.|  
  
## <a name="see-also"></a>См. также  
 [Объекты источников данных &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
