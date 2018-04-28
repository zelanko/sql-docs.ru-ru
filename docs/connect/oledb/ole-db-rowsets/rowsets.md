---
title: Наборы строк | Документы Microsoft
description: Наборы строк в драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 417514258d1300b14af81ba65628a342a57e9a56
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="rowsets"></a>Наборы строк
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Набор строк — это несколько строк, содержащих столбцы данных. Наборы строк — это основные объекты, позволяющие всем поставщикам данных OLE DB представлять данные результирующих наборов в виде таблиц.  
  
 После создания сеанса с помощью **IDBCreateSession::CreateSession** метод, потребитель может использовать либо **IOpenRowset** или **IDBCreateCommand** интерфейс для сеанса, чтобы создать набор строк. Драйвер OLE DB для SQL Server поддерживает оба интерфейса. Оба эти метода описаны здесь.  
  
-   Создать набор строк путем вызова **IOpenRowset::OpenRowset** метод.  
  
     Это эквивалентно созданию набора строк из одной таблицы. Этот метод открывает и возвращает набор строк, включающий все строки одной базовой таблицы. Один из аргументов **OpenRowset** — идентификатор таблицы, который идентифицирует таблицу, из которой создается набор строк.  
  
-   Создать командный объект, вызвав **IDBCreateCommand::CreateCommand** метод.  
  
     Объект команд выполняет команды, поддерживаемые поставщиком. С помощью драйвер OLE DB для SQL Server, потребитель может указать любую [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкции, например инструкцию SELECT или вызов хранимой процедуры. Создание набора строк с помощью объекта команд включает следующие шаги.  
  
    1.  Потребитель вызывает метод **IDBCreateCommand::CreateCommand** метод для сеанса, чтобы получить объект команд, запрашивающий **ICommandText** интерфейса на объект команды. Это **ICommandText** интерфейс задает и получает действительный текст команды. Потребитель заполняет текст команды путем вызова **ICommandText::SetCommandText** метод.  
  
    2.  Пользователь вызывает **ICommand::Execute** метод для команды. Объект набора строк, создаваемый во время выполнения команды, содержит результирующий набор этой команды.  
  
 Потребитель может использовать **ICommandProperties** интерфейс для получения или задания свойств набора строк, возвращаемого при выполнении команды по **ICommand::Execute** интерфейсов. Наиболее часто запрашиваемыми свойствами являются интерфейсы, которые должны поддерживаться набором строк. Кроме интерфейсов, потребитель может запросить свойства, изменяющие поведение набора строк или интерфейса.  
  
 Потребители освобождают наборы строк с **IRowset::Release** метод. При освобождении набора строк освобождаются все дескрипторы строк, удерживаемые потребителем для данного набора строк. При освобождении набора строк методы доступа не освобождаются. Если у вас есть **IAccessor** интерфейс, он по-прежнему имеет освобождается.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Создание набора строк с IOpenRowset](../../oledb/ole-db-rowsets/creating-a-rowset-with-iopenrowset.md)  
  
-   [Создание наборов строк с ICommand::Execute](../../oledb/ole-db-rowsets/creating-rowsets-with-icommand-execute.md)  
  
-   [Свойства набора строк и поведение](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
-   [Наборы строк и курсоры SQL Server](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)  
  
-   [Выборка строк](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
-   [Выборка одной строки при помощи интерфейса IRow](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
-   [Закладки](../../oledb/ole-db-rowsets/bookmarks.md)  
  
-   [Обновление данных в наборах строк](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>См. также  
 [Программирование драйвера OLE DB для SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
