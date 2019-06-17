---
title: Обновление данных в курсорах SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
ms.assetid: 732dafee-f2d5-4aef-aad7-3a8bf3b1e876
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b5c0b188d8fd45c1177cab77501bdf80fc550987
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63242919"
---
# <a name="updating-data-in-sql-server-cursors"></a>Обновление данных в курсорах SQL Server
  При выборке и обновлении данных через [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсоров, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приложение-потребитель поставщика OLE DB для собственного клиента ограничивается те же рекомендации и ограничения, применяемые для любого другого клиентского приложения.  
  
 В управлении параллельным доступом к данным участвуют только строки курсоров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда потребитель запрашивает изменяемый набор строк, управление параллелизмом осуществляется свойством DBPROP_LOCKMODE. Чтобы изменить уровень управления параллельным доступом, потребитель устанавливает свойство DBPROP_LOCKMODE до того, как открывает набор строк.  
  
 Уровни изоляции транзакции могут вызвать значительные задержки при позиционировании строк, если клиентское приложение оставляет транзакции долгое время открытыми. По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента использует уровень изоляции read committed, определяемое DBPROPVAL_TI_READCOMMITTED. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента поддерживает "грязных" изоляции read, если параллелизм набора строк только для чтения. Поэтому потребитель может запросить более высокий уровень изоляции в изменяемом наборе строк, но не может успешно запросить более низкий уровень.  
  
## <a name="immediate-and-delayed-update-modes"></a>Режимы немедленного и отложенного обновления  
 В режиме немедленного обновления каждый вызов метода **IRowsetChange::SetData** приводит к обмену данными с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если потребитель выполняет несколько изменений в одной строке, эффективнее будет осуществить все изменения в одном вызове функции **SetData**.  
  
 В режиме отложенного обновления обмен данными с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] осуществляется для каждой строки, указанной параметрами *cRows* и *rghRows* метода **IRowsetUpdate::Update**.  
  
 В каждом режиме обмен данными представляет отдельную транзакцию, если для набора строк отсутствует открытый объект транзакции.  
  
 При использовании **IRowsetUpdate::Update**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента пытается обработать каждую указанную строку. Ошибка, происходящая из-за недопустимых значений данных, длину или состояния для любой строки не останавливает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обработки поставщика OLE DB для собственного клиента. Можно изменить все строки, участвующие в обновлении, или ни одной. Потребитель должен изучить возращенный *prgRowStatus* массива, чтобы определить ошибку для каждой конкретной строки, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение DB_S_ERRORSOCCURRED, поставщик OLE DB для собственного клиента.  
  
 Потребитель не должен предполагать, что строки обрабатываются в каком-то определенном порядке. Если потребителю требуется упорядоченная обработка данных нескольких строк, он должен установить этот порядок в логике приложения и открыть транзакцию, содержащую процесс упорядочивания.  
  
## <a name="see-also"></a>См. также  
 [Обновление данных в наборах строк](updating-data-in-rowsets.md)  
  
  
