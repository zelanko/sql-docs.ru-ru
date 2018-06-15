---
title: Обработка нескольких результирующих наборов при помощи интерфейса IMultipleResults | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
ms.assetid: 754d3f30-7d94-4b67-8dac-baf2699ce9c6
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f3ab7376bcbb6b8237aa2600ac19fb5a13b6304f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32948639"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>Обработка нескольких результирующих наборов при помощи интерфейса IMultipleResults
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Потребители используют **IMultipleResults** интерфейс для обработки результатов, возвращенных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнение команды поставщика OLE DB для собственного клиента. Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента отправляет команду для выполнения, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет инструкции и возвращает результаты.  
  
 Клиент должен обработать все результаты выполнения команды. Поскольку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнение команды поставщика OLE DB для собственного клиента можно создать объекты с несколькими наборами строк в виде результатов, используйте **IMultipleResults** интерфейса, чтобы убедиться, что выполняется получение данных приложения инициированный клиентом кругового пути.  
  
 Следующие [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкция создает несколько наборов строк, некоторые содержат данные строк из **OrderDetails** таблицы, а некоторые – результаты предложения COMPUTE BY:  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 Если потребитель выполняет команду, содержащую этот текст, и запрашивает набор строк в качестве интерфейса возвращаемых результатов, возвращается только первый набор строк. Потребитель может обработать все строки в возвращенном наборе строк. Однако, если свойство источника данных DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_FALSE и режим MARS не включен для соединения, в объекте сеанса могут быть выполнены никакие другие команды ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента не будет создавать другой соединение), пока не будет отменена команда. Если режим MARS не включен в соединении, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента возвращает ошибку DB_E_OBJECTOPEN, если свойство DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_FALSE и вернет значение E_FAIL, если нет активной транзакции.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвратит также DB_E_OBJECTOPEN при использовании потоковых выходных параметров, приложение не потребило все данные, возвращенные значения параметров перед вызовом **IMultipleResults::GetResults**  для получения следующего набора результатов. Если режим MARS не включен и соединение занято выполнением команды, не производящей набор строк или производящей набор строк, который не является серверным курсором, а свойство источника данных DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Поставщик OLE DB создает дополнительные соединения для поддержки параллельных объектов команды, если транзакция является активной, в противном случае возвращает ошибку. Управление транзакциями и блокировками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] производит отдельно для каждого соединения. Если создано второе соединение, команда в отдельном соединении не использует общие блокировки. Необходимо соблюдать осторожность и убедиться, что одна команда не блокирует другую, удерживая блокировки строк, запрошенных другой командой. Если включен режим MARS, в одном соединении могут быть активными несколько команд, а если выполняются явные транзакции, все команды совместно используют общую транзакцию.  
  
 Потребитель может отменить команду с помощью [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) или освободив все удерживаемые ссылки на объект команды и производный набор строк.  
  
 С помощью **IMultipleResults** во всех экземплярах позволяет потребителю получить все наборы строк, сформированные при выполнении команды, а соответствующим образом определить, когда нужно отменить выполнение команды и освободить объект сеанса для использования другие команды.  
  
> [!NOTE]  
>  При использовании курсоров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнение команды создает курсор [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает успех или ошибку создания курсора, поэтому обмен данными с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершается по выполнении команды. Каждый **GetNextRows** вызова становится кругового пути. Таким образом, могут существовать несколько активных объектов команд, каждая из которых обрабатывает набор строк, являющийся результатом выборки из серверного курсора. Дополнительные сведения см. в разделе [наборы строк и курсоры SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>См. также  
 [Команды](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
