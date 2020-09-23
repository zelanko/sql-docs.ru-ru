---
title: Обновление данных в курсорах (драйвер OLE DB)
description: Сведения о том, как приложение-потребитель OLE DB Driver for SQL Server работает с запросами в изменяемом наборе строк, используя курсоры SQL Server.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eae7b9119803615a2d18fe4710ff1eda2b91ac5b
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88859927"
---
# <a name="updating-data-in-sql-server-cursors"></a>Обновление данных в курсорах SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  При выборке и обновлении данных с помощью курсоров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] приложение-потребитель OLE DB Driver for SQL Server связано теми же условиями и ограничениями, что и любое другое клиентское приложение.  
  
 В управлении параллельным доступом к данным участвуют только строки курсоров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Когда потребитель запрашивает изменяемый набор строк, управление параллелизмом осуществляется свойством DBPROP_LOCKMODE. Чтобы изменить уровень управления параллельным доступом, потребитель устанавливает свойство DBPROP_LOCKMODE до того, как открывает набор строк.  
  
 Уровни изоляции транзакции могут вызвать значительные задержки при позиционировании строк, если клиентское приложение оставляет транзакции долгое время открытыми. По умолчанию драйвер OLE DB для SQL Server использует уровень изоляции READ COMMITTED, указанный с помощью свойства DBPROPVAL_TI_READCOMMITTED. OLE DB Driver for SQL Server поддерживает изоляцию чтения "грязных" данных, если параллелизм набора строк находится в режиме только для чтения. Поэтому потребитель может запросить более высокий уровень изоляции в изменяемом наборе строк, но не может успешно запросить более низкий уровень.  
  
## <a name="immediate-and-delayed-update-modes"></a>Режимы немедленного и отложенного обновления  
 В режиме немедленного обновления каждый вызов метода **IRowsetChange::SetData** приводит к обмену данными с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если потребитель выполняет несколько изменений в одной строке, эффективнее будет осуществить все изменения в одном вызове функции **SetData**.  
  
 В режиме отложенного обновления обмен данными с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] осуществляется для каждой строки, указанной параметрами *cRows* и *rghRows* метода **IRowsetUpdate::Update**.  
  
 В каждом режиме обмен данными представляет отдельную транзакцию, если для набора строк отсутствует открытый объект транзакции.  
  
 При использовании метода **IRowsetUpdate::Update** OLE DB Driver for SQL Server пытается обработать каждую указанную строку. Ошибка, происходящая из-за недопустимых данных, длины или значений состояния для каждой строки, не останавливает эту обработку. Можно изменить все строки, участвующие в обновлении, или ни одной. Потребитель должен изучить возращенный массив *prgRowStatus*, чтобы определить ошибку для каждой конкретной строки, если драйвер OLE DB для SQL Server возвращает DB_S_ERRORSOCCURRED.  
  
 Потребитель не должен предполагать, что строки обрабатываются в каком-то определенном порядке. Если потребителю требуется упорядоченная обработка данных нескольких строк, он должен установить этот порядок в логике приложения и открыть транзакцию, содержащую процесс упорядочивания.  
  
## <a name="see-also"></a>См. также:  
 [Обновление данных в наборах строк](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
