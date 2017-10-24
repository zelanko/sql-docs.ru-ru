---
title: "Повторная синхронизация команды свойство динамические (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Resync Command property [ADO]
ms.assetid: 4e2bb601-0fe8-4d61-b00e-38341d85a6bb
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cfa4fee83eef9c17a7dfb1eae6dbad64be2c98ce
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="resync-command-property-dynamic-ado"></a>Повторная синхронизация команды свойство динамические (ADO)
Указывает команду, предоставленные пользователем строкой, которую [Resync](../../../ado/reference/ado-api/resync-method.md) проблем метода для обновления данных в таблице, указанной в [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) динамических свойств.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** равное командной строки.  
  
## <a name="remarks"></a>Замечания  
 [Записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект является результат операции СОЕДИНЕНИЯ, выполняется на нескольких базовых таблицах. Зависит от строк, затронутых *AffectRecords* параметр [Resync](../../../ado/reference/ado-api/resync-method.md) метод. Стандартные **Resync** метод выполняется в том случае, если [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) и **Resync команда** свойства не установлены.  
  
 Строка команды **Resync команда** свойство параметризированную команду или хранимую процедуру, которая однозначно определяет строку, на время обновления и возвращает одну строку, содержащую одно и то же количество и порядок столбцов в виде строки таблицы, обновляются. Командная строка содержит параметр для каждого столбца первичного ключа в **уникальной таблицы**; в противном случае возвращается ошибка во время выполнения. Параметры автоматически заполняется значений первичного ключа из строки для обновления.  
  
 Ниже приведены два примера, в зависимости от SQL.  
  
 1\) **записей** определяется с помощью команды:  
  
```  
SELECT * FROM Customers JOIN Orders ON   
   Customers.CustomerID = Orders.CustomerID  
   WHERE city = 'Seattle'  
   ORDER BY CustomerID  
```  
  
 **Resync команда** свойству:  
  
```  
"SELECT * FROM   
   (SELECT * FROM Customers JOIN Orders   
   ON Customers.CustomerID = Orders.CustomerID  
   city = 'Seattle' ORDER BY CustomerID)  
WHERE Orders.OrderID = ?"  
```  
  
 **Уникальной таблицы** — *заказов* и ее первичный ключ *OrderID*, является параметризованным. Подзапрос select предоставляет простой способ программными средствами убедитесь, что одно и то же количество и порядок столбцов возвращаются как командой исходного.  
  
 2\) **записей** определяется с помощью хранимой процедуры:  
  
```  
CREATE PROC Custorders @CustomerID char(5) AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID   
WHERE Customers.CustomerID = @CustomerID  
```  
  
 **Resync** метод должен выполнить следующую хранимую процедуру:  
  
```  
CREATE PROC CustordersResync @ordid int AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID  
WHERE Orders.ordid  = @ordid  
```  
  
 **Resync команда** свойству:  
  
```  
"{call CustordersResync (?)}"  
```  
  
 Опять же **уникальной таблицы** — *заказов* и ее первичный ключ *OrderID*, является параметризованным.  
  
 **Команда синхронизации** динамическое свойство добавляется к **записей** объекта [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции при [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству **adUseClient**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)

