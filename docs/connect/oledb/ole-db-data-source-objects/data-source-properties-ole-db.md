---
title: Свойства (OLE DB) источника данных | Документы Microsoft
description: Свойства источника данных (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- OLE DB data source properties [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a1cd2b8b72fc2806eeedab5585c8ad99449bbdf6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="data-source-properties-ole-db"></a>Свойства источника данных (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server реализует свойства источника данных следующим образом.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|DBPROP_CURRENTCATALOG|R Чтение и запись: чтение и запись по умолчанию: нет<br /><br /> Описание: Значение dbprop_currentcatalog указывает сообщает текущей базы данных для драйвера OLE DB для SQL Server сеанса. Задание значения свойства действует идентичные как задание текущей базы данных с помощью [!INCLUDE[tsql](../../../includes/tsql-md.md)] используйте *базы данных* инструкции.<br /><br /> Начиная с версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], при вызове [sp_defaultdb](../../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md) и укажите имя базы данных в нижнем регистре, даже если база данных была создана с именем в смешанном регистре, свойство DBPROP_CURRENTCATALOG возвратит имя в нижнем регистре. В предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] свойство DBPROP_CURRENTCATALOG возвращало имя в ожидаемом смешанном регистре.|  
|DBPROP_MULTIPLECONNECTIONS|По умолчанию R Чтение и запись: чтение и запись: VARIANT_FALSE<br /><br /> Описание: Если соединение выполняется команда, производящей набор строк или производящей набор строк, не являющегося серверный курсор, выполняется другая команда новое соединение будет создаваться для выполнения этой команды, если свойство DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_TRUE.<br /><br /> Драйвер OLE DB для SQL Server не создает другое соединение, если свойство DBPROP_MULTIPLECONNECTION имеет значение VARIANT_FALSE или если транзакция активна в соединении. Драйвер OLE DB для SQL Server возвращает значение DB_E_OBJECTOPEN, если свойство DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_FALSE и вернет значение E_FAIL, если нет активной транзакции. Управление транзакциями и блокировками [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] производит отдельно для каждого соединения. Если создано второе соединение, команды в отдельных соединениях не используют общие блокировки. Чтобы убедиться, что одна команда не блокирует другую, удерживайте блокировки строк, запрошенных другой командой. Это верно и при создании нескольких сеансов.<br /><br /> Каждый сеанс имеет отдельное соединение.|  
  
 В наборе данных от поставщика свойств DBPROPSET_SQLSERVERDATASOURCE драйвер OLE DB для SQL Server определяет следующие дополнительные свойства источника данных.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|SSPROP_ENABLEFASTLOAD|По умолчанию R Чтение и запись: чтение и запись: VARIANT_FALSE<br /><br /> Описание: Чтобы включить массовое копирование из памяти, свойство SSPROP_ENABLEFASTLOAD задавайте значение VARIANT_TRUE. Это свойство установлено в источнике данных, вновь созданный сеанс позволяет потребителю получить доступ к [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md) интерфейса.<br /><br /> Если свойство имеет значение VARIANT_TRUE, **IRowsetFastLoad** интерфейс доступен через **IOpenRowset::OpenRowset** , запрашивая **IID_IRowsetFastLoad** интерфейса или путем установки **SSPROP_IRowsetFastLoad** значение VARIANT_TRUE.|  
|SSPROP_ENABLEBULKCOPY|По умолчанию R Чтение и запись: чтение и запись: VARIANT_FALSE<br /><br /> Описание: Чтобы включить массовое копирование из файлов, свойству SSPROP_ENABLEBULKCOPY должно быть присвоено значение VARIANT_TRUE. Если это свойство установлено в источнике данных, потребитель получает доступ к интерфейсу IBCPSession с тем же уровнем, что и сеанс.<br /><br /> Свойство SSPROP_IRowsetFastLoad также должно быть установлено в значение VARIANT_TRUE.|  
  
## <a name="see-also"></a>См. также:  
 [Объекты источника данных & #40; OLE DB & #41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
