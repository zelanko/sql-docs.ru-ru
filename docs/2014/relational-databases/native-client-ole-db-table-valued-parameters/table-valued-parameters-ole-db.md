---
title: Возвращающие табличное значение параметры (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
ms.assetid: 4298b73d-615b-4d28-9843-03b4d5fc489e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a759ed6729ce066cbbd5b8c38043402195b62b98
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704582"
---
# <a name="table-valued-parameters-ole-db"></a>Возвращающие табличное значение параметры (OLE DB)
  В этом разделе описывается поддержка возвращающих табличное значение параметров в поставщике OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Параметры, возвращающие ](../native-client/features/table-valued-parameters-sql-server-native-client.md)табличное значение, &#40;SQL Server Native Client&#41;. Пример использования можно найти в статье [Использование возвращающих табличные значения параметров (OLE DB)](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md).  
  
## <a name="remarks"></a>Remarks  
 В настоящее время можно отправить многострочные данные на сервер как параметры для процедуры с наборами параметров (параметр DBPARAMS метода `ICommand::Execute`). При использовании набора параметров каждый элемент набора должен быть отправлен на сервер в отдельном запросе удаленного вызова процедур (RPC). Возвращающие табличное значение параметры обеспечивают похожую функциональность, но лучше интегрированы с сервером. При этом уменьшается число запросов RPC, а на сервере возможны операции, основанные на наборах.  
  
 Возвращающие табличное значение параметры поддерживаются в поставщике OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как объекты OLE DB `Rowset`. Любой объект `Rowset` может быть предоставлен потребителем (то есть клиентским приложением, которое использует поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) в качестве заполнителя для возвращающих табличное значение параметров. Возвращающие табличное значение параметры обрабатываются как параметры других типов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает интерфейсы создания, обнаружения, определения, привязки и схемы.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Создание набора строк возвращающего табличное значение параметра](table-valued-parameter-rowset-creation.md)  
  
-   [Обнаружение типа возвращающего табличное значение параметра](../../database-engine/dev-guide/table-valued-parameter-type-discovery.md)  
  
-   [Выполнение команд, содержащих возвращающие табличные значения параметры](executing-commands-containing-table-valued-parameters.md)  
  
-   [Вставка данных в параметры, возвращающие табличные значения](inserting-data-into-table-valued-parameters.md)  
  
-   [Наборы строк схемы, измененные для возвращающих табличное значение параметров OLE DB](schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [Поддержка типов параметров OLE DB, возвращающих табличные значения](ole-db-table-valued-parameter-type-support.md)  
  
-   [Поддержка типов параметров OLE DB, возвращающих табличные значения &#40;методы&#41;](ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [Поддержка типов параметров OLE DB, возвращающих табличные значения &#40;свойства&#41;](ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
