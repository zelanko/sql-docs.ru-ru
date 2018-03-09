---
title: "О свойствах OLE DB | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-provider
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- SQL Server Native Client OLE DB provider, properties
- properties [OLE DB]
- property values [SQL Server Native Client]
ms.assetid: 0b36a61e-b542-400d-a3d2-e6f643caf2c6
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7d07af86429ab414c4c324e07ef308634b8ec42a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="about-ole-db-properties"></a>О свойствах OLE DB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Потребитель может устанавливать значения свойств, чтобы запросить определенное поведение объекта. Например, потребитель использует свойства для указания интерфейса, который должен предоставить набор строк. Потребители получают значения свойств для определения возможностей объекта, например набора строк, сеанса или объекта источника данных.  
  
 Каждое свойство имеет значение, тип, описание и атрибут чтения/записи, а для свойств набора строк — признак того, применим ли набор строк к отдельным столбцам.  
  
 Свойство определяется по идентификатору GUID и целому числу, представляющему идентификатор свойства. Набор свойств — это набор всех свойств с одинаковым идентификатором GUID. Помимо стандартных свойств OLE DB задает, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента реализует наборы свойств от поставщика и свойства в них. Каждое свойство принадлежит одной или нескольким группам свойств. Группа свойств — это группа всех свойств, применимых к определенному объекту. Группой свойств может быть группа свойств инициализации, группа свойств источника данных, группа свойств сеанса, группа свойств набора строк, группа свойств таблицы и группа свойств столбца. Ниже представлены свойства каждой из этих групп свойств.  
  
 Установка значения свойства предполагает следующее.  
  
1.  Определения свойств, которым присваиваются значения.  
  
2.  Определение набора свойств, содержащего идентифицированные свойства.  
  
3.  Выделение ресурсов для массива структур DBPROPSET — по одной на каждый идентифицированный набор свойств.  
  
4.  Выделение ресурсов для массива структур DBPROP для каждого набора свойств. Количество элементов в каждом массиве определяется числом свойств (идентифицированных на шаге 1), принадлежащих конкретному набору свойств.  
  
5.  Заполнение структуры DBPROP для каждого свойства.  
  
6.  Заполнение сведений (идентификатор GUID, счетчик числа элементов и указатель на соответствующий массив DBPROP) в структуре DBPROPSET для каждого набора свойств.  
  
7.  Вызов метода для установки свойств и передачи счетчика и массива структур DBPROPSET.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложения поставщика OLE DB для собственного клиента SQL Server](../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)   
 [Свойства (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=112207)  
  
  
