---
title: "Работа с объектами базы данных | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- database objects [SMO]
- objects [SMO]
ms.assetid: 702fd63d-8734-4a02-872e-aecfb037c787
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 556403a013ee348e836c059ef9b246b4d5606a87
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2018
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
  
  
