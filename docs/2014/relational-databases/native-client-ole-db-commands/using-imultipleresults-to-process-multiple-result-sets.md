---
title: Обработка нескольких результирующих наборов с помощью интерфейса IMultipleResults | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
ms.assetid: 754d3f30-7d94-4b67-8dac-baf2699ce9c6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e160733e01c3df2063a57d61bb8178438d383e1a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63155024"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>Обработка нескольких результирующих наборов при помощи интерфейса IMultipleResults
  Потребители используют интерфейс **IMultipleResults** для обработки результатов, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращаемых выполнением команды поставщика OLE DB собственного клиента. Когда поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента отправляет команду для выполнения, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет инструкции и возвращает все результаты.  
  
 Клиент должен обработать все результаты выполнения команды. Так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнение команды поставщика OLE DB собственного клиента может создавать объекты с несколькими наборами строк в качестве результатов, используйте интерфейс **IMultipleResults** , чтобы убедиться, что получение данных приложением завершает циклическое обращение, инициированное клиентом.  
  
 Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] формирует несколько наборов строк, при этом некоторые содержат данные строк из таблицы **OrderDetails**, а некоторые — результаты предложения COMPUTE BY:  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 Если потребитель выполняет команду, содержащую этот текст, и запрашивает набор строк в качестве интерфейса возвращаемых результатов, возвращается только первый набор строк. Потребитель может обработать все строки в возвращенном наборе строк. Но если свойство источника данных DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_FALSE, а для соединения не включен режим MARS, никакие другие команды не могут быть выполнены в объекте сеанса (поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB не будет создавать другое подключение), пока команда не будет отменена. Если режим MARS не включен для соединения, поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB возвращает ошибку DB_E_OBJECTOPEN, если DBPROP_MULTIPLECONNECTIONS VARIANT_FALSE и возвращает E_FAIL при наличии активной транзакции.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента также возвращает DB_E_OBJECTOPEN при использовании потоковых выходных параметров, и приложение не потребляет все возвращенные значения выходного параметра перед вызовом **IMultipleResults::** GetNext для получения следующего результирующего набора. Если режим MARS не включен и соединение занято выполнением команды, которая не создает набор строк, или если свойство источника данных DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_TRUE, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента создает дополнительные соединения для поддержки параллельных объектов команд, если только транзакция не активна, и в этом случае возвращается ошибка. Управление транзакциями и блокировками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] производит отдельно для каждого соединения. Если создано второе соединение, команда в отдельном соединении не использует общие блокировки. Необходимо соблюдать осторожность и убедиться, что одна команда не блокирует другую, удерживая блокировки строк, запрошенных другой командой. Если включен режим MARS, в одном соединении могут быть активными несколько команд, а если выполняются явные транзакции, все команды совместно используют общую транзакцию.  
  
 Потребитель может отменить команду с помощью метода [ISSAbort::Abort](../native-client-ole-db-interfaces/issabort-abort-ole-db.md) или освободив все удерживаемые ссылки на объект команды и производный набор строк.  
  
 Использование интерфейса **IMultipleResults** во всех экземплярах позволяет потребителю получить все наборы строк, сформированные командой, и соответствующим образом определить, когда нужно отменить выполнение команды, чтобы освободить объект сеанса для других команд.  
  
> [!NOTE]  
>  При использовании курсоров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнение команды создает курсор [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает успех или ошибку создания курсора, поэтому обмен данными с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершается по выполнении команды. Следовательно, каждый вызов **GetNextRows** становится обменом данными. Таким образом, могут существовать несколько активных объектов команд, каждая из которых обрабатывает набор строк, являющийся результатом выборки из серверного курсора. Дополнительные сведения см. в статье [Наборы строк и курсоры SQL Server](../native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>См. также  
 [Команды](commands.md)  
  
  
