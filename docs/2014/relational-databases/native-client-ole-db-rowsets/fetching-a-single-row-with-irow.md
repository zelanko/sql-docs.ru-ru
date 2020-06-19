---
title: Выборка одной строки через IRow | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
ms.openlocfilehash: b5573fe1fef39f29329e373323f5f8aaf15f2c58
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055955"
---
# <a name="fetching-a-single-row-with-irow"></a>Выборка одной строки при помощи интерфейса IRow
  Реализация интерфейса **IRow** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственном поставщике OLE DB клиента упрощена для повышения производительности. Интерфейс **IRow** предоставляет прямой доступ к столбцам одного объекта, представляющего собой строку. Если заранее известно, что результатом выполнения команды будет ровно одна строка, **IRow** даст возможность получить столбцы этой строки. Если в результирующий набор входит несколько строк, интерфейс **IRow** предоставит доступ только к первой.  
  
 Реализация интерфейса **IRow** не позволяет перемещаться по строке. Доступ к каждому столбцу в строке осуществляется только один раз с одним исключением: доступ к столбцу можно получить один раз, чтобы найти размер столбца и снова получить данные.  
  
> [!NOTE]  
>  Метод **IRow::Open** поддерживает открытие только объектов типа DBGUID_STREAM или DBGUID_NULL.  
  
 Для получения объекта строки с помощью метода **ICommand::Execute** нужно передать в качестве параметра идентификатор IID_IRow. Обработка нескольких результирующих наборов производится с помощью интерфейса **IMultipleResults**. Интерфейс **IMultipleResults** поддерживает интерфейсы **IRow** и **IRowset**. Интерфейс **IRowset** используется для массовых операций.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Использование метода IRow::GetColumns](using-irow-getcolumns.md)  
  
-   [Выборка данных большого двоичного объекта при помощи интерфейса IRow](../../database-engine/dev-guide/fetching-blob-data-using-irow.md)  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк](rowsets.md)  
  
  
