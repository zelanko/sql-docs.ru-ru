---
title: Большие двоичные объекты и объекты OLE | Документы Microsoft
description: Большие двоичные объекты и объекты OLE
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-blobs
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- OLE DB Driver for SQL Server, BLOBs
- large data, OLE objects
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: cacbe007e9bf0187648ad1fd95c8b6616fb8a300
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2018
ms.locfileid: "35666084"
---
# <a name="blobs-and-ole-objects"></a>Большие двоичные объекты и объекты OLE
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server предоставляет **ISequentialStream** интерфейс для поддержки доступа потребителя к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **ntext**, **текст**, **изображения** , **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, и типы данных xml в двоичном виде больших объектов (BLOB). **Чтения** метод **ISequentialStream** позволяет потребителю получать большого объема данных в управляемых фрагментах.  
  
 Образец, демонстрирующий эту функцию, в разделе [большие объемы данных, задайте &#40;OLE DB&#41;](../../oledb/ole-db-how-to/set-large-data-ole-db.md).  
  
 Драйвер OLE DB для SQL Server можно использовать реализованный потребителем **IStorage** интерфейс, если потребитель предоставляет указатель на интерфейс в метод доступа, предназначенном для изменения данных.  
  
 Для типов данных большого объема, драйвер OLE DB для SQL Server проверяет наличие допущения размер типа в **IRowset** и интерфейсы DDL. Столбцы, имеющие **varchar**, **nvarchar**, и **varbinary** типов данных и неограниченным максимальным размером будут представлены как ISLONG через наборы строк схемы и через интерфейсы, возвращающие типы данных столбцов.  
  
 Драйвер OLE DB для SQL Server предоставляет **varchar(max)**, **varbinary(max)** и **nvarchar(max)** типами как DBTYPE_STR, DBTYPE_BYTES и DBTYPE_WSTR соответственно.  
  
 Работать с этими типами приложение может следующими способами.  
  
-   Выполните привязку, указав тип (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Если буфер недостаточно большой достаточно будет выполнено усечение — точно так же, как в предыдущих версиях (Хотя сейчас доступны большие значения).  
  
-   Выполните привязку, указав тип и задав DBTYPE_BYREF.  
  
-   Выполните привязку, указав тип DBTYPE_IUNKNOWN, и используйте потоковую передачу.  
  
 При привязке к DBTYPE_IUNKNOWN используется потоковая возможность ISequentialStream. Драйвер OLE DB для SQL Server поддерживает привязку выходных параметров как DBTYPE_IUNKNOWN для типов данных больших значений. Это необходимо для поддержки сценариев, где хранимая процедура возвращает эти типы данных в качестве возвращаемого значения, которые будут возвращены в виде DBTYPE_IUNKNOWN клиенту.  
  
## <a name="storage-object-limitations"></a>Ограничения объекта хранилища  
  
-   Драйвер OLE DB для SQL Server может поддерживать только один открытый объект хранилища. Пытается открыть более одного объекта хранилища (для получения ссылки на более чем одном **ISequentialStream** указатель на интерфейс) возвращается DBSTATUS_E_CANTCREATE.  
  
-   В драйвер OLE DB для SQL Server значение по умолчанию только для чтения свойства DBPROP_BLOCKINGSTORAGEOBJECTS равно VARIANT_TRUE. Таким образом Если объект хранилища активна, некоторые методы (Кроме методов в объектах хранилища) завершатся ошибкой E_UNEXPECTED.  
  
-   Длина данных, представленных объектом реализованный потребителем хранения должна быть известна драйвер OLE DB для SQL Server при создании метода доступа к строке, который ссылается на объект хранилища. Потребитель должен выполнить привязку признака длины в структуре DBBINDING, которая используется для создания метода доступа.  
  
-   Если строка содержит больше чем одно большое значение данных и DBPROP_ACCESSORDER не имеет значения DBPROPVAL_AO_RANDOM, потребитель либо необходимо использовать для извлечения данных в строке или обработать все больших значений данных перед получением других драйвер OLE DB для SQL Server строк, поддерживаемый курсорами значения строк. Если DBPROP_ACCESSORDER имеет значение DBPROPVAL_AO_RANDOM, драйвер OLE DB для SQL Server кэширует все типы данных xml как большие двоичные объекты (BLOB), чтобы он был доступен в любом порядке.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Возврат больших данных](../../oledb/ole-db-blobs/getting-large-data.md)  
  
-   [Присваивание больших данных](../../oledb/ole-db-blobs/setting-large-data.md)  
  
-   [Поддержка потоков для выходных параметров BLOB-объектов](../../oledb/ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для SQL Server программирования](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)        
 [Использование типов больших значений](../../oledb/features/using-large-value-types.md)  
  
  
