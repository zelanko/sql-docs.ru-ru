---
title: Обработка нескольких результирующих наборов при помощи интерфейса IMultipleResults | Документы Microsoft
description: Использование IMultipleResults для обработки нескольких результирующих наборов
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 162b706391e2128cb715396fd836bf446a625b17
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>Обработка нескольких результирующих наборов при помощи интерфейса IMultipleResults
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Потребители используют **IMultipleResults** интерфейс для обработки результатов, возвращенных драйвер OLE DB для выполнения команды SQL Server. Когда драйвер OLE DB для SQL Server отправляет команду для выполнения, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполняет инструкции и возвращает результаты.  
  
 Клиент должен обработать все результаты выполнения команды. Поскольку драйвер OLE DB для выполнения команды SQL Server можно создать объекты с несколькими наборами строк как результат, используйте **IMultipleResults** интерфейс, чтобы убедиться в окончании работы инициированный клиентом цикла обработки получение данных приложения.  
  
 Следующие [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкция создает несколько наборов строк, некоторые содержат данные строк из **OrderDetails** таблицы, а некоторые – результаты предложения COMPUTE BY:  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 Если потребитель выполняет команду, содержащую этот текст, и запрашивает набор строк в качестве интерфейса возвращаемых результатов, возвращается только первый набор строк. Потребитель может обработать все строки в возвращенном наборе строк. Однако, если свойство источника данных DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_FALSE и режим MARS не включен для соединения, другие команды не могут быть выполнены в объекте сеанса (драйвер OLE DB для SQL Server не создает другого соединения) до Команда отменена. Если в соединении не включен режим MARS, драйвер OLE DB для SQL Server возвращает ошибку DB_E_OBJECTOPEN, если свойство DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_FALSE и вернет значение E_FAIL, если нет активной транзакции.  
  
 Драйвер OLE DB для SQL Server возвратит также DB_E_OBJECTOPEN при использовании потоковых выходных параметров, приложение не потребило все данные, возвращенные значения параметров перед вызовом **IMultipleResults::GetResults** для Получите к следующему результирующему набору. Если режим MARS не включен и соединение занято выполнением команды, производящей набор строк или производящей набор строк, который не является серверным курсором и если свойство источника данных DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_TRUE, драйвер OLE DB для SQL Server создает дополнительные соединения для поддержки параллельных объектов команды, если транзакция является активной, в противном случае возвращает ошибку. Управление транзакциями и блокировками [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] производит отдельно для каждого соединения. Если создано второе соединение, команда в отдельном соединении не использует общие блокировки. Необходимо соблюдать осторожность и убедиться, что одна команда не блокирует другую, удерживая блокировки строк, запрошенных другой командой. Если включен режим MARS, в одном соединении могут быть активными несколько команд, а если выполняются явные транзакции, все команды совместно используют общую транзакцию.  
  
 Потребитель может отменить команду с помощью [ISSAbort::Abort](../../oledb/ole-db-interfaces/issabort-abort-ole-db.md) или освободив все удерживаемые ссылки на объект команды и производный набор строк.  
  
 С помощью **IMultipleResults** во всех экземплярах позволяет потребителю получить все наборы строк, сформированные при выполнении команды, а соответствующим образом определить, когда нужно отменить выполнение команды и освободить объект сеанса для использования другие команды.  
  
> [!NOTE]  
>  При использовании курсоров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполнение команды создает курсор [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращает успех или ошибку создания курсора, поэтому обмен данными с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] завершается по выполнении команды. Каждый **GetNextRows** вызова становится кругового пути. Таким образом, могут существовать несколько активных объектов команд, каждая из которых обрабатывает набор строк, являющийся результатом выборки из серверного курсора. Дополнительные сведения см. в разделе [наборы строк и курсоры SQL Server](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>См. также  
 [Команды](../../oledb/ole-db-commands/commands.md)  
  
  
