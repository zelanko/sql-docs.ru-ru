---
title: Получение одной строки с помощью IRow | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c73bb76df097d259422f2c5626ecfb08668036c6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73761746"
---
# <a name="fetching-a-single-row-with-irow"></a>Выборка одной строки при помощи интерфейса IRow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Реализация интерфейса **IRow** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственном поставщике OLE DB клиента упрощена для повышения производительности. **IRow** обеспечивает прямой доступ к столбцам одного объекта строки. Если заранее известно, что результатом выполнения команды будет ровно одна строка, **IRow** даст возможность получить столбцы этой строки. Если в результирующий набор входит несколько строк, интерфейс **IRow** предоставит доступ только к первой.  
  
 Реализация интерфейса **IRow** не позволяет перемещаться по строке. Доступ к каждому столбцу в строке осуществляется только один раз с одним исключением: доступ к столбцу можно получить один раз, чтобы найти размер столбца и снова получить данные.  
  
> [!NOTE]  
>  Метод **IRow::Open** поддерживает открытие только объектов типа DBGUID_STREAM или DBGUID_NULL.  
  
 Для получения объекта строки с помощью метода **ICommand::Execute** нужно передать в качестве параметра идентификатор IID_IRow. Обработка нескольких результирующих наборов производится с помощью интерфейса **IMultipleResults**. **IMultipleResults** поддерживает **IRow** и **IRowset**. **IRowset** используется для выполнения операций с массовыми операциями.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Использование метода IRow::GetColumns](../../relational-databases/native-client-ole-db-rowsets/using-irow-getcolumns.md)  
  
-   [Выборка данных большого двоичного объекта при помощи интерфейса IRow](https://msdn.microsoft.com/library/badbd6ac-20aa-4891-a14f-48d38e7f30de)  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
