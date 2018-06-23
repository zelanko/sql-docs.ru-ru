---
title: Большие двоичные объекты и объекты OLE | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 767fa2f6-9cd2-436f-add5-e760bed29a58
caps.latest.revision: 42
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a4c6a32f003206d9d1d92944c3ec8b1a6f48076a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192231"
---
# <a name="blobs-and-ole-objects"></a>Большие двоичные объекты и объекты OLE
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет **ISequentialStream** интерфейс для поддержки доступа потребителя к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**, **текст**, **изображения**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, и типы данных xml в двоичном виде больших объектов (BLOB-объекты ). **Чтения** метод **ISequentialStream** позволяет потребителю получать большого объема данных в управляемых фрагментах.  
  
 Образец, демонстрирующий эту функцию, в разделе [большие объемы данных, задайте &#40;OLE DB&#41;](../native-client-ole-db-how-to/set-large-data-ole-db.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента может использовать реализованный потребителем **IStorage** интерфейс, если потребитель предоставляет указатель на интерфейс в метод доступа, предназначенном для изменения данных.  
  
 Для типов данных больших значений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента проверяет наличие допущения размер типа в **IRowset** и интерфейсы DDL. Столбцы с **varchar**, **nvarchar**, и **varbinary** типов данных с неограниченным максимальным размером будут представлены как ISLONG через наборы строк схемы и интерфейсы Возвращает типы данных столбцов.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет **varchar(max)**, **varbinary(max)** и **nvarchar(max)** типы как DBTYPE_STR, DBTYPE_BYTES и DBTYPE_ WSTR соответственно.  
  
 Для работы с этими типами приложение имеет следующие возможности.  
  
-   Выполните привязку, указав тип (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Если буфер недостаточно большой, будет выполнено усечение — точно так же, как в предыдущих версиях (хотя сейчас доступны большие значения).  
  
-   Выполните привязку, указав тип и задав DBTYPE_BYREF.  
  
-   Выполните привязку, указав тип DBTYPE_IUNKNOWN, и используйте потоковую передачу.  
  
 При привязке к DBTYPE_IUNKNOWN используется потоковая возможность ISequentialStream. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента поддерживает привязку выходных параметров как DBTYPE_IUNKNOWN для типов данных больших значений облегчить ситуацию, когда хранимая процедура возвращает эти данные типы значений, которые будут представлены как DBTYPE_IUNKNOWN клиенту.  
  
## <a name="storage-object-limitations"></a>Ограничения объекта хранилища  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента может поддерживать только один открытый объект хранилища. Пытается открыть более одного объекта хранилища (для получения ссылки на более чем одном **ISequentialStream** указатель на интерфейс) возвращается DBSTATUS_E_CANTCREATE.  
  
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента, значение по умолчанию только для чтения свойства DBPROP_BLOCKINGSTORAGEOBJECTS имеет значение VARIANT_TRUE. Оно указывает, что если имеется активный объект хранилища, некоторые методы (не относящиеся к объектам хранилища) завершатся ошибкой E_UNEXPECTED.  
  
-   Длина данных, представленных объектом реализованный потребителем хранения должна быть известна для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента при создании метода доступа к строке, который ссылается на объект хранилища. Потребитель должен выполнить привязку признака длины в структуре DBBINDING, которая используется для создания метода доступа.  
  
-   Если строка содержит больше, чем значение одного большого объема данных и DBPROP_ACCESSORDER не имеет значения DBPROPVAL_AO_RANDOM, потребитель должен использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] значения строк поставщика поддержкой курсора OLE DB для собственного клиента для получения данных в строке или обрабатывать все большие объемы данных до получить значения других строк. Если DBPROP_ACCESSORDER имеет значение DBPROPVAL_AO_RANDOM, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента кэширует все типы данных xml как большие двоичные объекты (BLOB), чтобы он был доступен в любом порядке.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Возврат больших данных](getting-large-data.md)  
  
-   [Присваивание больших данных](setting-large-data.md)  
  
-   [Поддержка потоков для выходных параметров BLOB-объектов](streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Использование типов больших значений](../native-client/features/using-large-value-types.md)  
  
  