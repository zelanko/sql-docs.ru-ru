---
title: Большие двоичные объекты и OLE | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 767fa2f6-9cd2-436f-add5-e760bed29a58
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b4e284d2086684af232c17b59675b834b26f497b
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73790639"
---
# <a name="blobs-and-ole-objects"></a>Большие двоичные объекты и объекты OLE
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB предоставляет интерфейс **ISequentialStream** для поддержки доступа потребителя к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**, **Text**, **Image**, **varchar (max)** , **nvarchar (max)** , **varbinary (max).** и типы данных XML как большие двоичные объекты (BLOB). Метод **Read** интерфейса **ISequentialStream** позволяет потребителю получать большой объем данных в виде фрагментов данных, с которыми удобно работать.  
  
 Пример, демонстрирующий эту функцию, см. в разделе [Set &#40;Large&#41;Data OLE DB](../../relational-databases/native-client-ole-db-how-to/set-large-data-ole-db.md).  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB может использовать реализуемый потребителем интерфейс **IStorage** , когда потребитель предоставляет указатель интерфейса в методе доступа, связанном с изменением данных.  
  
 Для типов данных больших значений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB проверяет предположения о размере типов в интерфейсах **IRowset** и DDL. Столбцы с типами данных **varchar**, **nvarchar**и **varbinary** с максимальным размером, установленным в значение unlimited, будут представлены как длинные через наборы строк схемы и интерфейсы, возвращающие типы данных столбцов.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB предоставляет типы **varchar (max)** , **varbinary (max)** и **nvarchar (max)** как DBTYPE_STR, DBTYPE_BYTES и DBTYPE_WSTR соответственно.  
  
 Для работы с этими типами приложение имеет следующие возможности.  
  
-   Выполните привязку, указав тип (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Если буфер недостаточно большой, будет выполнено усечение — точно так же, как в предыдущих версиях (хотя сейчас доступны большие значения).  
  
-   Выполните привязку, указав тип и задав DBTYPE_BYREF.  
  
-   Выполните привязку, указав тип DBTYPE_IUNKNOWN, и используйте потоковую передачу.  
  
 При привязке к DBTYPE_IUNKNOWN используется потоковая возможность ISequentialStream. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB поддерживает привязку выходных параметров как DBTYPE_IUNKNOWN для типов данных больших значений, чтобы упростить сценарии, в которых хранимая процедура возвращает эти типы данных в качестве возвращаемых значений, которые будут предоставлены клиенту как DBTYPE_IUNKNOWN.  
  
## <a name="storage-object-limitations"></a>Ограничения объекта хранилища  
  
-   Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB может поддерживать только один открытый объект хранилища. При попытке открыть несколько объектов хранилища (получить ссылку на несколько указателей интерфейса **ISequentialStream**) возвращается DBSTATUS_E_CANTCREATE.  
  
-   В поставщике [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB значение по умолчанию свойства DBPROP_BLOCKINGSTORAGEOBJECTS только для чтения — VARIANT_TRUE. Оно указывает, что если имеется активный объект хранилища, некоторые методы (не относящиеся к объектам хранилища) завершатся ошибкой E_UNEXPECTED.  
  
-   Длина данных, представленных объектом хранилища, реализованным потребителем, должна быть известна [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика собственного клиента OLE DB при создании метода доступа к строке, ссылающегося на объект хранилища. Потребитель должен выполнить привязку признака длины в структуре DBBINDING, которая используется для создания метода доступа.  
  
-   Если строка содержит больше одного большого значения данных, а DBPROP_ACCESSORDER не DBPROPVAL_AO_RANDOM, потребитель должен либо использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент OLE DB поставщика с поддержкой курсора, чтобы получить данные строк или обработать все большие значения данных перед получением других значений строк. Если DBPROP_ACCESSORDER DBPROPVAL_AO_RANDOM, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент OLE DBный поставщик кэширует все типы данных XML как большие двоичные объекты (BLOB), чтобы к ним можно было обращаться в любом порядке.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Возврат больших данных](../../relational-databases/native-client-ole-db-blobs/getting-large-data.md)  
  
-   [Присваивание больших данных](../../relational-databases/native-client-ole-db-blobs/setting-large-data.md)  
  
-   [Поддержка потоков для выходных параметров BLOB-объектов](../../relational-databases/native-client-ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>См. также статью  
 [SQL Server Native Client &#40;OLE DB&#41; ](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Использование типов больших значений](../../relational-databases/native-client/features/using-large-value-types.md)  
  
  
