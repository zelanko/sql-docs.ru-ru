---
title: Получение нескольких наборов записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- receiving multiple Recordsets [ADO]
- Recordset object [ADO], receiving multiple Recordsets
ms.assetid: 2a7ad7a6-f00d-4355-b0b5-d0ab957b0566
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6d6e649201b8bf23a1b696d574baea2f4b049e06
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924535"
---
# <a name="receiving-multiple-recordsets"></a>Получение нескольких наборов записей
[Поставщик OLE DB Майкрософт для SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) поддерживает возврат нескольких объектов **Recordset** для одной команды, содержащей несколько инструкций SQL, по одному **набору записей** на каждую инструкцию SQL. Порядок, в котором возвращаются **наборы записей**, соответствует порядку, в котором инструкции SQL помещаются в текст команды.  
  
 Поставщик OLE DB Майкрософт для SQL Server также возвращает несколько результирующих наборов в ADO, если команда содержит предложение COMPUTE. Например, команда, содержащая следующую инструкцию SQL, возвращает результаты в двух объектах **набора записей** : один для набора строк (*ProductID*, *ProductName*, *UnitPrice*), а другой — для средней цены всех продуктов в таблице.  
  
```  
SELECT ProductID, ProductName, UnitPrice   
  FROM PRODUCTS   
  COMPUTE AVG(UnitPrice)  
```  
  
 Для перечисления этих двух объектов можно использовать метод **Recordset. NextRecordset** .  
  
 Дополнительные сведения см. в разделе [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md).
