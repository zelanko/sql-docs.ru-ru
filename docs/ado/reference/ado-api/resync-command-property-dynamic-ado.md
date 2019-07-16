---
title: Повторная синхронизация команды свойство (динамическое) (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Resync Command property [ADO]
ms.assetid: 4e2bb601-0fe8-4d61-b00e-38341d85a6bb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e81fa9ffb28ba31f50d77cacf372bc24d09787ba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917139"
---
# <a name="resync-command-property-dynamic-ado"></a>Свойство Resync Command (динамическое) (ADO)
Указывает пользовательские команды-строка, [Resync](../../../ado/reference/ado-api/resync-method.md) проблем метода для обновления данных в таблице, указанной в [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) динамических свойств.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, которое является командной строкой.  
  
## <a name="remarks"></a>Примечания  
 [Записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта является результатом операции СОЕДИНЕНИЯ выполняются на несколько базовых таблиц. Зависят от строк, затронутых *AffectRecords* параметр [Resync](../../../ado/reference/ado-api/resync-method.md) метод. Стандартный **Resync** метод выполняется в том случае, если [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) и **Resync команда** свойства не заданы.  
  
 Строка команды **Resync команда** свойство параметризованную команду или хранимую процедуру, которая однозначно определяет строку к обновлению и возвращает одну строку, содержащую разное число и порядок столбцов в виде строки таблицы, обновляются. Строка команды содержит параметр для каждого столбца первичного ключа в **уникальной таблицы**; в противном случае возвращается ошибка времени выполнения. Параметры заполняются автоматически значений первичного ключа из строки для обновления.  
  
 Ниже приведены два примера, на основе SQL.  
  
 1\) **записей** определяется с помощью команды:  
  
```  
SELECT * FROM Customers JOIN Orders ON   
   Customers.CustomerID = Orders.CustomerID  
   WHERE city = 'Seattle'  
   ORDER BY CustomerID  
```  
  
 **Resync команда** свойство имеет значение:  
  
```  
"SELECT * FROM   
   (SELECT * FROM Customers JOIN Orders   
   ON Customers.CustomerID = Orders.CustomerID  
   city = 'Seattle' ORDER BY CustomerID)  
WHERE Orders.OrderID = ?"  
```  
  
 **Уникальной таблицы** — *заказы* и ее первичный ключ *OrderID*, является параметризованным. Подзапрос select предоставляет простой способ программным образом обеспечить разное число и порядок столбцов возвращаются как и в случае с помощью исходной команды.  
  
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
  
 **Resync команда** свойство имеет значение:  
  
```  
"{call CustordersResync (?)}"  
```  
  
 Опять же **уникальной таблицы** — *заказы* и ее первичный ключ *OrderID*, является параметризованным.  
  
 **Команда синхронизации** динамическое свойство добавляется к **записей** объект [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции при [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству **adUseClient**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
