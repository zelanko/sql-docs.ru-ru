---
title: Изменение формы | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- reshaping previously shaped Recordset [ADO]
- data shaping [ADO], reshaping
ms.assetid: b1c965b7-3dad-4de6-9e0e-502ca8785be3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 324801cbfc97db4e2a1137fa04df0c74dc1897a1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63280395"
---
# <a name="reshaping"></a>Изменение формы данных
Объект **набор записей** создан с помощью предложения фигуры могут быть выделены команды *псевдоним* (обычно с ключевым словом AS). Псевдоним фигурной **записей** можно ссылаться в совершенно другую команду. То есть вы можете повторно использовать, или *reshape*, ранее фигурной **записей** в новую команду фигуры. Для поддержки этой возможности, ADO предоставляет свойство [изменить форму имени](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md).  
  
 Изменение формы имеет две основные функции. Первый способ — связать существующий **записей** элемента новым родительским элементом **записей**.  
  
## <a name="example"></a>Пример  
  
```  
rs1.Open "SHAPE {select * from Customers} " & _  
         "APPEND ({select * from Orders} AS chapOrders " & _  
         "RELATE CustomerID to CustomerID)", cn  
  
rs2.Open "SHAPE {select * from Employees} " & _  
         "APPEND (chapOrders RELATE EmployeeID to EmployeeID)", cn  
```  
  
 Вторая функция — для доступа к не разбит на разделы для существующих дочерних **набор записей** объекты, используя синтаксис «ФИГУРЫ \<записей reshape name >».  
  
> [!NOTE]
>  Не удается добавить столбцы к существующему **набор записей**, изменить форму параметризованную **набор записей** или **набор записей** объекты в любые промежуточные предложение COMPUTE и выполнить Статистическая обработка операций на любом **записей** потомком **записей** прежних требований подверглись преобразованию. **Записей** изменили форму и его команда должны использовать же [подключения](../../../ado/reference/ado-api/connection-object-ado.md).  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)
