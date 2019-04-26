---
title: Возвращающие табличные значения параметров (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
ms.assetid: 4298b73d-615b-4d28-9843-03b4d5fc489e
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eb03ccfd661fb4d80be605363e314381403a460b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62640078"
---
# <a name="table-valued-parameters-ole-db"></a>Возвращающие табличное значение параметры (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  В этом разделе описывается поддержка возвращающих табличное значение параметров в поставщике OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [возвращающего табличное значение параметров &#40;собственный клиент SQL Server&#41;](../../relational-databases/native-client/features/table-valued-parameters-sql-server-native-client.md). Пример, см. в разделе [параметров, возвращающих &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md).  
  
## <a name="remarks"></a>Примечания  
 В настоящее время многострочные данные можно отправлять на сервер как параметры процедуры с наборами параметров (параметр DBPARAMS метода **ICommand::Execute**). При использовании набора параметров каждый элемент набора должен быть отправлен на сервер в отдельном запросе удаленного вызова процедур (RPC). Возвращающие табличное значение параметры обеспечивают похожую функциональность, но лучше интегрированы с сервером. При этом уменьшается число запросов RPC, а на сервере возможны операции, основанные на наборах.  
  
 Возвращающие табличное значение параметры поддерживаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный поставщик OLE DB клиента как OLE DB **набора строк** объектов. Любой **набора строк** объектом-получателем может быть передан объект (то есть клиентское приложение, использующее [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный поставщик OLE DB клиента) как заполнитель для параметров, возвращающих табличные значения параметров. Возвращающие табличное значение параметры обрабатываются как параметры других типов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает интерфейсы создания, обнаружения, определения, привязки и схемы.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Создание набора строк возвращающего табличное значение параметра](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)  
  
-   [Обнаружение типа возвращающего табличное значение параметра](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md)  
  
-   [Выполнение команд, содержащих возвращающие табличные значения параметры](../../relational-databases/native-client-ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md)  
  
-   [Вставка данных в параметры, возвращающие табличные значения](../../relational-databases/native-client-ole-db-table-valued-parameters/inserting-data-into-table-valued-parameters.md)  
  
-   [Наборы строк схемы, измененные для возвращающих табличное значение параметров OLE DB](../../relational-databases/native-client-ole-db-table-valued-parameters/schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [Поддержка типов параметров OLE DB, возвращающих табличные значения](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)  
  
-   [Поддержка типов параметров OLE DB, возвращающих табличные значения &#40;методы&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [Поддержка типов параметров OLE DB, возвращающих табличные значения &#40;свойства&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
