---
title: Большие двоичные объекты и объекты OLE | Документация Майкрософт
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
ms.openlocfilehash: d6f2a73f44d762a2d17eccc8cf82570b07933426
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68128894"
---
# <a name="blobs-and-ole-objects"></a>Большие двоичные объекты и объекты OLE
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет **ISequentialStream** интерфейс для поддержки доступа потребителя к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**, **текст**, **изображение**, **varchar(max)** , **nvarchar(max)** , **varbinary(max)** , и типы данных xml в виде двоичного кода больших объектов (больших двоичных объектов ). Метод **Read** интерфейса **ISequentialStream** позволяет потребителю получать большой объем данных в виде фрагментов данных, с которыми удобно работать.  
  
 Образец, демонстрирующий эту функцию, см. в разделе [набор больших данных &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/set-large-data-ole-db.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента может использовать реализованный потребителем **IStorage** привязан интерфейс, если потребитель предоставляет указатель на интерфейс в метод доступа для изменения данных.  
  
 Для типов данных больших значений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента проверяет наличие предположения размер типа в **IRowset** и интерфейсы DDL. Столбцы с **varchar**, **nvarchar**, и **varbinary** типы данных с максимальным размером, заданным в неограниченное будут представлены как ISLONG через наборы строк схемы и интерфейсы Возвращение типов данных столбцов.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет **varchar(max)** , **varbinary(max)** и **nvarchar(max)** типы как DBTYPE_STR, DBTYPE_BYTES и DBTYPE_ WSTR соответственно.  
  
 Для работы с этими типами приложение имеет следующие возможности.  
  
-   Выполните привязку, указав тип (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Если буфер недостаточно большой, будет выполнено усечение — точно так же, как в предыдущих версиях (хотя сейчас доступны большие значения).  
  
-   Выполните привязку, указав тип и задав DBTYPE_BYREF.  
  
-   Выполните привязку, указав тип DBTYPE_IUNKNOWN, и используйте потоковую передачу.  
  
 При привязке к DBTYPE_IUNKNOWN используется потоковая возможность ISequentialStream. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента поддерживает привязку выходных параметров как DBTYPE_IUNKNOWN для типов данных больших значений облегчить ситуацию, где хранимая процедура возвращает эти данные типы как возвращаемые значения, которые будут представлены как DBTYPE_IUNKNOWN клиенту.  
  
## <a name="storage-object-limitations"></a>Ограничения объекта хранилища  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента может поддерживать только один открытый объект хранилища. При попытке открыть несколько объектов хранилища (получить ссылку на несколько указателей интерфейса **ISequentialStream**) возвращается DBSTATUS_E_CANTCREATE.  
  
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента, значение по умолчанию только для чтения свойства DBPROP_BLOCKINGSTORAGEOBJECTS имеет значение VARIANT_TRUE. Оно указывает, что если имеется активный объект хранилища, некоторые методы (не относящиеся к объектам хранилища) завершатся ошибкой E_UNEXPECTED.  
  
-   Длина данных, представленный объект хранилища, реализованный потребителем должна быть известна для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента, когда создается методом доступа к строке, который ссылается на объект хранилища. Потребитель должен выполнить привязку признака длины в структуре DBBINDING, которая используется для создания метода доступа.  
  
-   Если строка содержит больше одного большого значения данных и DBPROP_ACCESSORDER не имеет значения DBPROPVAL_AO_RANDOM, потребитель должен либо использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB для собственного клиента поставщика строк, поддерживаемый курсорами для извлечения строки данных или обработки данных все большие значения перед получить значения других строк. Если DBPROP_ACCESSORDER имеет значение DBPROPVAL_AO_RANDOM, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента кэширует все типы данных xml в виде больших двоичных объектов (BLOB), таким образом, чтобы он доступен в любом порядке.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Возврат больших данных](../../relational-databases/native-client-ole-db-blobs/getting-large-data.md)  
  
-   [Присваивание больших данных](../../relational-databases/native-client-ole-db-blobs/setting-large-data.md)  
  
-   [Поддержка потоков для выходных параметров BLOB-объектов](../../relational-databases/native-client-ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Использование типов больших значений](../../relational-databases/native-client/features/using-large-value-types.md)  
  
  
