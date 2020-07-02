---
title: Сведения о свойствах OLE DB | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- SQL Server Native Client OLE DB provider, properties
- properties [OLE DB]
- property values [SQL Server Native Client]
ms.assetid: 0b36a61e-b542-400d-a3d2-e6f643caf2c6
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9197b1f947640dfc925ed037294eb9def2abb1da
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785163"
---
# <a name="about-ole-db-properties"></a>О свойствах OLE DB
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Потребитель может устанавливать значения свойств, чтобы запросить определенное поведение объекта. Например, потребитель использует свойства для указания интерфейса, который должен предоставить набор строк. Потребители получают значения свойств для определения возможностей объекта, например набора строк, сеанса или объекта источника данных.  
  
 Каждое свойство имеет значение, тип, описание и атрибут чтения/записи, а для свойств набора строк — признак того, применим ли набор строк к отдельным столбцам.  
  
 Свойство определяется по идентификатору GUID и целому числу, представляющему идентификатор свойства. Набор свойств — это набор всех свойств с одинаковым идентификатором GUID. В дополнение к стандартным наборам свойств OLE DB, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента реализует в них наборы свойств и свойства, относящиеся к поставщику. Каждое свойство принадлежит одной или нескольким группам свойств. Группа свойств — это группа всех свойств, применимых к определенному объекту. Группой свойств может быть группа свойств инициализации, группа свойств источника данных, группа свойств сеанса, группа свойств набора строк, группа свойств таблицы и группа свойств столбца. Ниже представлены свойства каждой из этих групп свойств.  
  
 Установка значения свойства предполагает следующее.  
  
1.  Определения свойств, которым присваиваются значения.  
  
2.  Определение набора свойств, содержащего идентифицированные свойства.  
  
3.  Выделение ресурсов для массива структур DBPROPSET — по одной на каждый идентифицированный набор свойств.  
  
4.  Выделение ресурсов для массива структур DBPROP для каждого набора свойств. Количество элементов в каждом массиве определяется числом свойств (идентифицированных на шаге 1), принадлежащих конкретному набору свойств.  
  
5.  Заполнение структуры DBPROP для каждого свойства.  
  
6.  Заполнение сведений (идентификатор GUID, счетчик числа элементов и указатель на соответствующий массив DBPROP) в структуре DBPROPSET для каждого набора свойств.  
  
7.  Вызов метода для установки свойств и передачи счетчика и массива структур DBPROPSET.  
  
## <a name="see-also"></a>См. также  
 [Создание приложения поставщика SQL Server Native Client OLE DB](../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)   
 [Свойства (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=112207)  
  
  
