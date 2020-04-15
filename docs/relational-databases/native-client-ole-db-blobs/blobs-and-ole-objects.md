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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d0cb9751940489513f939ab8ee52728c6b75e925
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297704"
---
# <a name="blobs-and-ole-objects"></a>Большие двоичные объекты и объекты OLE
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB предоставляет интерфейс **ISequentialStream** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для поддержки доступа потребителей к **ntext,** **тексту,** **изображению,** **varchar(max)**, **nvarchar(max),** **varbinary/max)** и типам данных xml как бинарные крупные объекты (BLOB). Метод **Read** интерфейса **ISequentialStream** позволяет потребителю получать большой объем данных в виде фрагментов данных, с которыми удобно работать.  
  
 Образец приложения, демонстрирующий эту возможность, см. в статье [Задание данных больших объектов (OLE DB)](../../relational-databases/native-client-ole-db-how-to/set-large-data-ole-db.md).  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB может использовать реализованный потребителем интерфейс **IStorage,** когда потребитель предоставляет указатель интерфейса в аксессуаре, связанном для изменения данных.  
  
 Для больших типов значений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных поставщик Native Client OLE DB проверяет предположения размера в интерфейсах **IRowset** и DDL. Столбцы с **varchar,** **nvarchar**и **варбинарными** типами данных с максимальным размером, установленным на неограниченный размер, будут представлены как ISLONG через наборы схем и интерфейсы, возвращающие типы данных столбцов.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB предоставляет **варчаров (макс),** **варбинарные (макс)** и **nvarchar (max)** типы, как DBTYPE_STR, DBTYPE_BYTES и DBTYPE_WSTR соответственно.  
  
 Для работы с этими типами приложение имеет следующие возможности.  
  
-   Выполните привязку, указав тип (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Если буфер недостаточно большой, будет выполнено усечение — точно так же, как в предыдущих версиях (хотя сейчас доступны большие значения).  
  
-   Выполните привязку, указав тип и задав DBTYPE_BYREF.  
  
-   Выполните привязку, указав тип DBTYPE_IUNKNOWN, и используйте потоковую передачу.  
  
 При привязке к DBTYPE_IUNKNOWN используется потоковая возможность ISequentialStream. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB поддерживает обязательные параметры вывода, так как DBTYPE_IUNKNOWN для типов данных большого значения, чтобы облегчить сценарии, в которых сохраненная процедура возвращает эти типы данных в виде значений возврата, которые будут подвергаться DBTYPE_IUNKNOWN клиенту.  
  
## <a name="storage-object-limitations"></a>Ограничения объекта хранилища  
  
-   Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB может поддерживать только один открытый объект хранения данных. При попытке открыть несколько объектов хранилища (получить ссылку на несколько указателей интерфейса **ISequentialStream**) возвращается DBSTATUS_E_CANTCREATE.  
  
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщике Native Client OLE DB значение DBPROP_BLOCKINGSTORAGEOBJECTS только для чтения является VARIANT_TRUE. Оно указывает, что если имеется активный объект хранилища, некоторые методы (не относящиеся к объектам хранилища) завершатся ошибкой E_UNEXPECTED.  
  
-   Длина данных, представленных объектом хранения, реализованным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителем, должна быть известна поставщику Native Client OLE DB при создании доступа к строке, который ссылается на объект хранения. Потребитель должен выполнить привязку признака длины в структуре DBBINDING, которая используется для создания метода доступа.  
  
-   Если строка содержит более одного большого значения данных и DBPROP_ACCESSORDER [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не является DBPROPVAL_AO_RANDOM, потребитель должен либо использовать курсор-поддерживаемый поставщиком строки Native Client OLE DB для извлечения данных строки, либо обработать все значения больших данных, прежде чем получить другие значения строки. Если DBPROP_ACCESSORDER DBPROPVAL_AO_RANDOM, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB кэширует все типы данных xml как двоичные крупные объекты (BLOBs), так что к ним можно получить доступ в любом порядке.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Возврат больших данных](../../relational-databases/native-client-ole-db-blobs/getting-large-data.md)  
  
-   [Присваивание больших данных](../../relational-databases/native-client-ole-db-blobs/setting-large-data.md)  
  
-   [Поддержка потоков для выходных параметров BLOB](../../relational-databases/native-client-ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>См. также:  
 [Родной клиент сервера &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Использование типов больших значений](../../relational-databases/native-client/features/using-large-value-types.md)  
  
  
