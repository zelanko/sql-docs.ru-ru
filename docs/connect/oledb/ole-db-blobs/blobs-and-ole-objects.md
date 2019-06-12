---
title: Большие двоичные объекты и объекты OLE | Документация Майкрософт
description: Большие двоичные объекты и объекты OLE
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- OLE DB Driver for SQL Server, BLOBs
- large data, OLE objects
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 0cc1f42d438c7216cf9b1f6f9ee9167747447e66
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66800700"
---
# <a name="blobs-and-ole-objects"></a>Большие двоичные объекты и объекты OLE
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server предоставляет интерфейс **ISequentialStream** для поддержки доступа потребителя к типам данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **ntext**, **text**, **image**, **varchar(max)** , **nvarchar(max)** , **varbinary(max)** и xml как к большим двоичным объектам (BLOB). Метод **Read** интерфейса **ISequentialStream** позволяет потребителю получать большой объем данных в виде фрагментов данных, с которыми удобно работать.  
  
 Образец, демонстрирующий эту функцию, см. в разделе [набор больших данных &#40;OLE DB&#41;](../../oledb/ole-db-how-to/set-large-data-ole-db.md).  
  
 Драйвер OLE DB для SQL Server может использовать реализованный потребителем интерфейс **IStorage**, если потребитель предоставляет указатель на него в методе доступа, предназначенном для изменения данных.  
  
 В случае с типами данных больших значений драйвер OLE DB для SQL Server проверяет размер типа, который предполагают интерфейс **IRowset** и интерфейсы DDL. Столбцы с типами данных **varchar**, **nvarchar** и **varbinary** и неограниченным максимальным размером будут представлены как ISLONG через наборы строк схемы и интерфейсы, возвращающие типы данных столбца.  
  
 Драйвер OLE DB для SQL Server представляет типы данных **varchar(max)** , **varbinary(max)** и **nvarchar(max)** как DBTYPE_STR, DBTYPE_BYTES и DBTYPE_WSTR соответственно.  
  
 Работать с этими типами приложение может следующими способами.  
  
-   Выполните привязку, указав тип (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Если буфер недостаточно большой, будет выполнено усечение точно так же, как в предыдущих версиях (хотя сейчас доступны большие значения).  
  
-   Выполните привязку, указав тип и задав DBTYPE_BYREF.  
  
-   Выполните привязку, указав тип DBTYPE_IUNKNOWN, и используйте потоковую передачу.  
  
 При привязке к DBTYPE_IUNKNOWN используется потоковая возможность ISequentialStream. Драйвер OLE DB для SQL Server поддерживает привязку выходных параметров как DBTYPE_IUNKNOWN для типов данных больших значений. Это необходимо для поддержки сценариев, где хранимая процедура возвращает эти типы данных в качестве возвращаемых значений, которые возвращаются клиенту как тип DBTYPE_IUNKNOWN.  
  
## <a name="storage-object-limitations"></a>Ограничения объекта хранилища  
  
-   Драйвер OLE DB для SQL Server может поддерживать только один открытый объект хранилища. При попытке открыть несколько объектов хранилища (получить ссылку на несколько указателей интерфейса **ISequentialStream**) возвращается DBSTATUS_E_CANTCREATE.  
  
-   В драйвере OLE DB для SQL Server значением по умолчанию для свойства DBPROP_BLOCKINGSTORAGEOBJECTS, предназначенного только для чтения, является VARIANT_TRUE. Поэтому если имеется активный объект хранилища, некоторые методы (не относящиеся к объектам хранилища) завершатся ошибкой E_UNEXPECTED.  
  
-   Длина данных, представляемых объектами хранилища, которые реализует потребитель, должна быть известна драйверу OLE DB для SQL Server при создании метода доступа к строке, ссылающегося на объект хранилища. Потребитель должен выполнить привязку признака длины в структуре DBBINDING, которая используется для создания метода доступа.  
  
-   Если строка содержит несколько одиночных значений больших типов данных и DBPROP_ACCESSORDER не имеет значения DBPROPVAL_AO_RANDOM, потребитель должен либо использовать набор строк с поддержкой курсоров драйвера OLE DB для SQL Server, чтобы получить данные строк, либо обработать все значения больших типов данных, прежде чем получить значения других строк. Если DBPROP_ACCESSORDER имеет значение DBPROPVAL_AO_RANDOM, драйвер OLE DB для SQL Server кэширует все типы данных xml как большие двоичные объекты (BLOB), чтобы они были доступны в любом порядке.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Возврат больших данных](../../oledb/ole-db-blobs/getting-large-data.md)  
  
-   [Присваивание больших данных](../../oledb/ole-db-blobs/setting-large-data.md)  
  
-   [Поддержка потоков для выходных параметров BLOB-объектов](../../oledb/ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>См. также:  
 [Программирование драйвера OLE DB для SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)        
 [Использование типов больших значений](../../oledb/features/using-large-value-types.md)  
  
  
