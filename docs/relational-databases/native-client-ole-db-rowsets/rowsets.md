---
title: Наборы строк | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
ms.assetid: 5e7b3cbe-3670-4e18-8172-2226e0b6b142
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: da51990e310b7903ce90d0369e30ff098103e141
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300264"
---
# <a name="rowsets"></a>Наборы строк
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Набор строк — это несколько строк, содержащих столбцы данных. Наборы строк — это основные объекты, позволяющие всем поставщикам данных OLE DB представлять данные результирующих наборов в виде таблиц.  
  
 После создания сеанса с помощью метода **IDBCreateSession::CreateSession** потребитель может использовать интерфейс **IOpenRowset** или **IDBCreateCommand** этого сеанса для создания набора строк. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB поддерживает оба этих интерфейса. Оба эти метода описаны здесь.  
  
-   Создайте набор строк, вызвав метод **IOpenRowset::OpenRowset**.  
  
     Это эквивалентно созданию набора строк из одной таблицы. Этот метод открывает и возвращает набор строк, включающий все строки одной базовой таблицы. Одним из аргументов метода **OpenRowset** является идентификатор таблицы, указывающий таблицу, на основе которой создается набор строк.  
  
-   Создайте объект команд с помощью метода **IDBCreateCommand::CreateCommand**.  
  
     Объект команд выполняет команды, поддерживаемые поставщиком. С помощью поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребитель может указать любую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)], например SELECT, или вызов хранимой процедуры. Создание набора строк с помощью объекта команд включает следующие шаги.  
  
    1.  Потребитель вызывает метод **IDBCreateCommand::CreateCommand** для сеанса, чтобы получить объект команд, запрашивающий интерфейс **ICommandText** для объекта команд. Этот интерфейс **ICommandText** задает и получает действительный текст команды. Потребитель заполняет текст команды путем вызова метода **ICommandText::SetCommandText**.  
  
    2.  Пользователь вызывает метод **ICommand::Execute** для команды. Объект набора строк, создаваемый во время выполнения команды, содержит результирующий набор этой команды.  
  
 Потребитель может использовать интерфейс **ICommandProperties** для получения или задания свойств набора строк, возвращаемого командой, которая выполняется интерфейсом **ICommand::Execute**. Наиболее часто запрашиваемыми свойствами являются интерфейсы, которые должны поддерживаться набором строк. Кроме интерфейсов, потребитель может запросить свойства, изменяющие поведение набора строк или интерфейса.  
  
 Потребители освобождают наборы строк с помощью метода **IRowset::Release**. При освобождении набора строк освобождаются все дескрипторы строк, удерживаемые потребителем для данного набора строк. При освобождении набора строк методы доступа не освобождаются. Если используется интерфейс **IAccessor**, его нужно освободить отдельно.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Создание набора строк с помощью интерфейса IOpenRowset](../../relational-databases/native-client-ole-db-rowsets/creating-a-rowset-with-iopenrowset.md)  
  
-   [Создание наборов строк с помощью метода ICommand::Execute](../../relational-databases/native-client-ole-db-rowsets/creating-rowsets-with-icommand-execute.md)  
  
-   [Свойства и поведение наборов строк](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
-   [Наборы строк и курсоры SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md)  
  
-   [Выборка строк](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [Выборка одной строки с помощью интерфейса IRow](../../relational-databases/native-client-ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
-   [Закладки](../../relational-databases/native-client-ole-db-rowsets/bookmarks.md)  
  
-   [Обновление данных в строках](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client (OLE DB)](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
