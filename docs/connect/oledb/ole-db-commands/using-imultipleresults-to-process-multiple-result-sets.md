---
title: Обработка нескольких результирующих наборов с помощью интерфейса IMultipleResults | Документы Майкрософт
description: Обработка нескольких результирующих наборов с помощью интерфейса IMultipleResults
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: d5ea43d5607dc999bfbcc85d821167c6cdd8ae96
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47643662"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>Обработка нескольких результирующих наборов при помощи интерфейса IMultipleResults
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Потребители используют интерфейс **IMultipleResults** для обработки результатов, возвращенных командой драйвера OLE DB для SQL Server. Когда драйвер OLE DB для SQL Server отправляет команду для выполнения, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполняет инструкции и возвращает результаты.  
  
 Клиент должен обработать все результаты выполнения команды. Так как команда драйвера OLE DB для SQL Server может формировать в качестве результата несколько объектов набора строк, интерфейс **IMultipleResults** используется, чтобы приложение гарантированно завершило обмен данными, инициированный клиентом.  
  
 Следующая инструкция [!INCLUDE[tsql](../../../includes/tsql-md.md)] формирует несколько наборов строк, при этом некоторые содержат данные строк из таблицы **OrderDetails**, а некоторые — результаты предложения COMPUTE BY:  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 Если потребитель выполняет команду, содержащую этот текст, и запрашивает набор строк в качестве интерфейса возвращаемых результатов, возвращается только первый набор строк. Потребитель может обработать все строки в возвращенном наборе строк. Но если свойство источника данных DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_FALSE, а для соединения не включена функция MARS, в объекте сеанса невозможно будет выполнить ни одну другую команду (драйвер OLE DB для SQL Server не создает другого соединения), пока не будет отменена команда. Если в соединении не включена функция MARS, драйвер OLE DB для SQL Server возвращает ошибку DB_E_OBJECTOPEN, если свойство DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_FALSE, и возвращает E_FAIL, если отсутствует активная транзакция.  
  
 Драйвер OLE DB для SQL Server возвратит также DB_E_OBJECTOPEN при использовании потоковых выходных параметров, если приложение не потребило все возвращенные значения параметров вывода перед вызовом метода **IMultipleResults::GetResults** для получения следующего результирующего набора. Если функция MARS не включена и соединение занято выполнением команды, не предоставляющей набор строк или предоставляющей набор строк, который не является серверным курсором, а свойство источника данных DBPROP_MULTIPLECONNECTIONS имеет значение VARIANT_TRUE, драйвер OLE DB для SQL Server создает дополнительные соединения для поддержки параллельных объектов команды при отсутствии активной транзакции. В противном случае возвращается ошибка. Управление транзакциями и блокировками [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] производит отдельно для каждого соединения. Если создано второе соединение, команда в отдельном соединении не использует общие блокировки. Необходимо соблюдать осторожность и убедиться, что одна команда не блокирует другую, удерживая блокировки строк, запрошенных другой командой. Если включен режим MARS, в одном соединении могут быть активными несколько команд, а если выполняются явные транзакции, все команды совместно используют общую транзакцию.  
  
 Потребитель может отменить команду с помощью метода [ISSAbort::Abort](../../oledb/ole-db-interfaces/issabort-abort-ole-db.md) или освободив все удерживаемые ссылки на объект команды и производный набор строк.  
  
 Использование интерфейса **IMultipleResults** во всех экземплярах позволяет потребителю получить все наборы строк, сформированные командой, и соответствующим образом определить, когда нужно отменить выполнение команды, чтобы освободить объект сеанса для других команд.  
  
> [!NOTE]  
>  При использовании курсоров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполнение команды создает курсор [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращает успех или ошибку создания курсора, поэтому обмен данными с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] завершается по выполнении команды. Следовательно, каждый вызов **GetNextRows** становится обменом данными. Таким образом, могут существовать несколько активных объектов команд, каждая из которых обрабатывает набор строк, являющийся результатом выборки из серверного курсора. Дополнительные сведения см. в статье [Наборы строк и курсоры SQL Server](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>См. также:  
 [Команды](../../oledb/ole-db-commands/commands.md)  
  
  
