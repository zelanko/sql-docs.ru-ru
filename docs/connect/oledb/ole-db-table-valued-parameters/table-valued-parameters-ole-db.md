---
title: Возвращающие табличные значения параметров (OLE DB) | Документы Microsoft
description: Возвращающие табличное значение параметры (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4cddcc6ce6efb2697f1d6ae9d77f750ad64108d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="table-valued-parameters-ole-db"></a>Возвращающие табличное значение параметры (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В этом разделе описывается поддержка возвращающих табличные значения параметров в драйвер OLE DB для SQL Server. Дополнительные сведения см. в разделе [табличное значение параметры &#40;драйвер OLE DB для SQL Server&#41;](../../oledb/features/table-valued-parameters-oledb-driver-for-sql-server.md). Пример см. в разделе [использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md).  
  
## <a name="remarks"></a>Замечания  
 В настоящее время можно отправить многострочные данные на сервер в качестве параметров для процедуры с наборами параметров (параметр dbparams МЕТОДА **ICommand::Execute**). При использовании набора параметров каждый элемент набора должен быть отправлен на сервер в отдельном запросе удаленного вызова процедур (RPC). Возвращающие табличное значение параметры обеспечивают похожую функциональность, но лучше интегрированы с сервером. Уменьшает количество запросов RPC и включает операции на основе набора на сервере.  
  
 Возвращающие табличное значение параметры поддерживаются в драйвер OLE DB для SQL Server в качестве OLE DB **строк** объектов. Любой **строк** удалось предоставить объект потребителем (то есть в клиентском приложении с помощью драйвера OLE DB для SQL Server) как заполнитель для параметров, возвращающих табличные значения параметра. Возвращающие табличное значение параметры обрабатываются как параметры других типов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Драйвер OLE DB для SQL Server предоставляет создания, обнаружения, спецификации, привязки и схемы интерфейсов.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Создание набора строк возвращающего табличное значение параметра](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)  
  
-   [Обнаружение типа возвращающего табличное значение параметра](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md)  
  
-   [Выполнение команд, содержащих возвращающие табличные значения параметры](../../oledb/ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md)  
  
-   [Вставка данных в параметры, возвращающие табличные значения](../../oledb/ole-db-table-valued-parameters/inserting-data-into-table-valued-parameters.md)  
  
-   [Наборы строк схемы, измененные для возвращающих табличное значение параметров OLE DB](../../oledb/ole-db-table-valued-parameters/schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [Поддержка типов параметров OLE DB, возвращающих табличные значения](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)  
  
-   [Поддержка типов OLE DB табличное значение параметра &#40;методы&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [Поддержка типов OLE DB табличное значение параметра &#40;свойства&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для SQL Server программирования](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [Использование возвращающих табличные значения параметры & #40; OLE DB & #41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
