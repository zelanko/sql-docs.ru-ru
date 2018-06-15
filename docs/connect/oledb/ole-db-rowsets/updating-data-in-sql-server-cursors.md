---
title: Обновление данных в курсорах SQL Server | Документы Microsoft
description: Обновление данных в курсорах SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 321700be33a81b511f30af7e7b263bd188e54264
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307713"
---
# <a name="updating-data-in-sql-server-cursors"></a>Обновление данных в курсорах SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  При выборке и обновлении данных через [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] курсоров драйвер OLE DB для SQL Server, приложение-потребитель, ограничивается рекомендации и ограничения, применяемые для любого клиентского приложения.  
  
 В управлении параллельным доступом к данным участвуют только строки курсоров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Когда потребитель запрашивает изменяемый набор строк, управление параллелизмом осуществляется свойством DBPROP_LOCKMODE. Чтобы изменить уровень управления параллельным доступом, потребитель устанавливает свойство DBPROP_LOCKMODE до того, как открывает набор строк.  
  
 Уровни изоляции транзакции могут вызвать значительные задержки при позиционировании строк, если клиентское приложение оставляет транзакции долгое время открытыми. По умолчанию драйвер OLE DB для SQL Server использует уровень изоляции read committed, заданный в DBPROPVAL_TI_READCOMMITTED. Драйвер OLE DB для SQL Server поддерживает изоляции «грязные» чтения, если параллелизм набора строк доступно только для чтения. Поэтому потребитель может запросить более высокий уровень изоляции в изменяемом наборе строк, но не может успешно запросить более низкий уровень.  
  
## <a name="immediate-and-delayed-update-modes"></a>Режимы немедленного и отложенного обновления  
 В режиме немедленного обновления при каждом вызове функции **IRowsetChange::SetData** приводит к обмену данными [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если потребитель выполняет несколько изменений для одной строки, он эффективнее будет осуществить все изменения в одном **SetData** вызова.  
  
 В режиме отложенного обновления обмен данными выполняется [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для каждой строки, указанной в *cRows* и *rghRows* параметры **IRowsetUpdate::Update**.  
  
 В каждом режиме обмен данными представляет отдельную транзакцию, если для набора строк отсутствует открытый объект транзакции.  
  
 При использовании **IRowsetUpdate::Update**, драйвер OLE DB для SQL Server пытается обработать каждую указанную строку. Ошибка, происходящая из-за недопустимые значения для каждой строки данных, длину или состояние, не останавливает драйвер OLE DB для обработки в SQL Server. Можно изменить все строки, участвующие в обновлении, или ни одной. Потребитель должен изучить возращенный *prgRowStatus* массива, чтобы определить ошибку для любой конкретной строки, когда драйвер OLE DB для SQL Server возвращает DB_S_ERRORSOCCURRED.  
  
 Потребитель не должен предполагать, что строки обрабатываются в каком-то определенном порядке. Если потребителю требуется упорядоченная обработка данных нескольких строк, он должен установить этот порядок в логике приложения и открыть транзакцию, содержащую процесс упорядочивания.  
  
## <a name="see-also"></a>См. также  
 [Обновление данных в наборах строк](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
