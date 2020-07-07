---
title: Обновление данных в курсорах SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5627da0643b35bac430e59d9cbc0685ac6f44e38
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86013081"
---
# <a name="updating-data-in-sql-server-cursors"></a>Обновление данных в курсорах SQL Server
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  При выборке и обновлении данных с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсоров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приложение-потребитель поставщика собственного клиента OLE DB связывается с теми же соображениями и ограничениями, которые применяются к любому другому клиентскому приложению.  
  
 В управлении параллельным доступом к данным участвуют только строки курсоров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда потребитель запрашивает изменяемый набор строк, управление параллелизмом осуществляется свойством DBPROP_LOCKMODE. Чтобы изменить уровень управления параллельным доступом, потребитель устанавливает свойство DBPROP_LOCKMODE до того, как открывает набор строк.  
  
 Уровни изоляции транзакции могут вызвать значительные задержки при позиционировании строк, если клиентское приложение оставляет транзакции долгое время открытыми. По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента использует уровень изоляции READ COMMITTED, заданный DBPROPVAL_TI_READCOMMITTED. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента поддерживает изоляцию "грязного" чтения, если параллелизм набора строк доступен только для чтения. Поэтому потребитель может запросить более высокий уровень изоляции в изменяемом наборе строк, но не может успешно запросить более низкий уровень.  
  
## <a name="immediate-and-delayed-update-modes"></a>Режимы немедленного и отложенного обновления  
 В режиме немедленного обновления каждый вызов метода **IRowsetChange::SetData** приводит к обмену данными с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если потребитель выполняет несколько изменений в одной строке, эффективнее будет осуществить все изменения в одном вызове функции **SetData**.  
  
 В режиме отложенного обновления обмен данными с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] осуществляется для каждой строки, указанной параметрами *cRows* и *rghRows* метода **IRowsetUpdate::Update**.  
  
 В каждом режиме обмен данными представляет отдельную транзакцию, если для набора строк отсутствует открытый объект транзакции.  
  
 При использовании **IRowsetUpdate:: Update** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент OLE DB поставщика пытается обработать каждую указанную строку. Ошибка из-за недопустимых данных, длины или значений состояния для любой строки не останавливает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обработку поставщика собственного клиента OLE DB. Можно изменить все строки, участвующие в обновлении, или ни одной. Потребитель должен проверить возвращаемый массив *пргровстатус* , чтобы определить сбой для какой-либо конкретной строки, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB возвращает DB_S_ERRORSOCCURRED.  
  
 Потребитель не должен предполагать, что строки обрабатываются в каком-то определенном порядке. Если потребителю требуется упорядоченная обработка данных нескольких строк, он должен установить этот порядок в логике приложения и открыть транзакцию, содержащую процесс упорядочивания.  
  
## <a name="see-also"></a>См. также  
 [Обновление данных в наборах строк](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
