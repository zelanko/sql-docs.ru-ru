---
title: IMultipleResults, несколько наборов результатов
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
ms.assetid: 754d3f30-7d94-4b67-8dac-baf2699ce9c6
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c5e19cef4e00fc1c55e29e51ccea13c2fdb7a0e2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304457"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>Обработка нескольких результирующих наборов при помощи интерфейса IMultipleResults
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Потребители используют интерфейс **IMultipleResults** для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обработки результатов, возвращенных выполнением команды поставщика Native Client OLE DB. Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB отправляет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] команду для выполнения, выполняет операторы и возвращает любые результаты.  
  
 Клиент должен обработать все результаты выполнения команды. Поскольку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнение команды поставщика multiple rowset в качестве результатов может генерировать многорядные объекты, используйте интерфейс **IMultipleResults,** чтобы гарантировать, что поиск данных приложения завершает поездку в оба конца.  
  
 Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] формирует несколько наборов строк, при этом некоторые содержат данные строк из таблицы **OrderDetails**, а некоторые — результаты предложения COMPUTE BY:  
  
```sql
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 Если потребитель выполняет команду, содержащую этот текст, и запрашивает набор строк в качестве интерфейса возвращаемых результатов, возвращается только первый набор строк. Потребитель может обработать все строки в возвращенном наборе строк. Но если свойство источника DBPROP_MULTIPLECONNECTIONS данных настроено на VARIANT_FALSE, а MARS не включено в соединение, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] никакие другие команды не могут быть выполнены на объекте сеанса (поставщик Native Client OLE DB не создаст другого соединения) до тех пор, пока команда не будет отменена. Если MARS не включен в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соединение, поставщик Native Client OLE DB возвращает ошибку DB_E_OBJECTOPEN, если DBPROP_MULTIPLECONNECTIONS VARIANT_FALSE и возвращает E_FAIL, если есть активная транзакция.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB также возвращает DB_E_OBJECTOPEN при использовании streamed параметров вывода, и приложение не потребляет все значения возвратных параметров вывода до вызова **IMultipleResults::GetResults,** чтобы получить следующий набор результатов. Если MARS не включен и соединение занято запуском команды, которая не производит строку или которая производит строку, которая не является курсором сервера, и если свойство источника DBPROP_MULTIPLECONNECTIONS данных установлено для VARIANT_TRUE, поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB создает дополнительные соединения для поддержки одновременных командных объектов, если транзакция не активна, и в этом случае он возвращает ошибку. Управление транзакциями и блокировками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] производит отдельно для каждого соединения. Если создано второе соединение, команда в отдельном соединении не использует общие блокировки. Необходимо соблюдать осторожность и убедиться, что одна команда не блокирует другую, удерживая блокировки строк, запрошенных другой командой. Если включен режим MARS, в одном соединении могут быть активными несколько команд, а если выполняются явные транзакции, все команды совместно используют общую транзакцию.  
  
 Потребитель может отменить команду с помощью метода [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) или освободив все удерживаемые ссылки на объект команды и производный набор строк.  
  
 Использование интерфейса **IMultipleResults** во всех экземплярах позволяет потребителю получить все наборы строк, сформированные командой, и соответствующим образом определить, когда нужно отменить выполнение команды, чтобы освободить объект сеанса для других команд.  
  
> [!NOTE]  
>  При использовании курсоров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнение команды создает курсор [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает успех или ошибку создания курсора, поэтому обмен данными с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершается по выполнении команды. Следовательно, каждый вызов **GetNextRows** становится обменом данными. Таким образом, могут существовать несколько активных объектов команд, каждая из которых обрабатывает набор строк, являющийся результатом выборки из серверного курсора. Дополнительные сведения см. в статье [Наборы строк и курсоры SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>См. также:  
 [Команды](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
