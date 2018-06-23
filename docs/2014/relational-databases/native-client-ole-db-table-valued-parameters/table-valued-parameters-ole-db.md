---
title: Возвращающие табличные значения параметров (OLE DB) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
ms.assetid: 4298b73d-615b-4d28-9843-03b4d5fc489e
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1a3a4e683887022c905fd2faf45cf5ff36b57a3a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192867"
---
# <a name="table-valued-parameters-ole-db"></a>Возвращающие табличное значение параметры (OLE DB)
  В этом разделе описывается поддержка возвращающих табличное значение параметров в поставщике OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [табличное значение параметры &#40;собственный клиент SQL Server&#41;](../native-client/features/table-valued-parameters-sql-server-native-client.md). Пример см. в разделе [использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md).  
  
## <a name="remarks"></a>Примечания  
 В настоящее время можно отправить многострочные данные на сервер как параметры для процедуры с наборами параметров (параметр DBPARAMS метода `ICommand::Execute`). При использовании набора параметров каждый элемент набора должен быть отправлен на сервер в отдельном запросе удаленного вызова процедур (RPC). Возвращающие табличное значение параметры обеспечивают похожую функциональность, но лучше интегрированы с сервером. При этом уменьшается число запросов RPC, а на сервере возможны операции, основанные на наборах.  
  
 Возвращающие табличное значение параметры поддерживаются в поставщике OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как объекты OLE DB `Rowset`. Любой объект `Rowset` может быть предоставлен потребителем (то есть клиентским приложением, которое использует поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) в качестве заполнителя для возвращающих табличное значение параметров. Возвращающие табличное значение параметры обрабатываются как параметры других типов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает интерфейсы создания, обнаружения, определения, привязки и схемы.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Создание набора строк возвращающего табличное значение параметра](table-valued-parameter-rowset-creation.md)  
  
-   [Обнаружение типа возвращающего табличное значение параметра](../../database-engine/dev-guide/table-valued-parameter-type-discovery.md)  
  
-   [Выполнение команд, содержащих возвращающие табличные значения параметры](executing-commands-containing-table-valued-parameters.md)  
  
-   [Вставка данных в параметры, возвращающие табличные значения](inserting-data-into-table-valued-parameters.md)  
  
-   [Наборы строк схемы, измененные для возвращающих табличное значение параметров OLE DB](schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [Поддержка типов параметров OLE DB, возвращающих табличные значения](ole-db-table-valued-parameter-type-support.md)  
  
-   [Поддержка типов OLE DB табличное значение параметра &#40;методы&#41;](ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [Поддержка типов OLE DB табличное значение параметра &#40;свойства&#41;](ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  