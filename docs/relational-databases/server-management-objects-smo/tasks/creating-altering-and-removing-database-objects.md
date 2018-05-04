---
title: Работа с объектами базы данных | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- database objects [SMO]
- objects [SMO]
ms.assetid: 702fd63d-8734-4a02-872e-aecfb037c787
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 85a37e419a1b129083e25acad3f57d3e8f598949
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="creating-altering-and-removing-database-objects"></a>Создание, изменение и удаление объектов базы данных
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Создание объектов SMO включает следующие этапы:  
  
1.  создание экземпляра объекта;  
  
2.  настройка свойств объекта;  
  
3.  создание экземпляров дочерних объектов;  
  
4.  настройка свойств дочерних объектов;  
  
5.  создание объекта.  
  
 При создании в программе SMO экземпляров объектов SMO они не будут существовать в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , пока не будет вызван метод **Create** . Однако не обязательно запускать метод **Create** для каждого отдельного объекта. Если объект имеет набор дочерних объектов, метод **Create** необходимо вызвать только для родительского объекта. Например, при определении таблицы требуется, чтобы она содержала хотя бы один столбец. А столбец, в свою очередь, не может существовать без таблицы. Ниже представлена связь между таблицей и ее столбцами.  
  
 Метод <xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A> позволяет вносить изменения в объект. Несколько изменений объекта, например добавление дочерних объектов к одному из объектов коллекции или изменение значения свойства, объединяются в пакет и выполняются как одно изменение. Метод **Alter** уменьшает сетевой трафик и повышает общую производительность.  
  
 Инструкция **Drop** используется для удаления объекта и всех взаимозависимых дочерних объектов, которые требовались для первоначального создания объекта.  
  
## <a name="see-also"></a>См. также  
 [Модель объектов SMO](../../../relational-databases/server-management-objects-smo/smo-object-model.md)  
  
  
