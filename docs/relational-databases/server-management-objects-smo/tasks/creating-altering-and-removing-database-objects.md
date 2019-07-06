---
title: Работа с объектами базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- database objects [SMO]
- objects [SMO]
ms.assetid: 702fd63d-8734-4a02-872e-aecfb037c787
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c79ccb4805030cb93e67fa335e72de4d5984a62a
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67583579"
---
# <a name="creating-altering-and-removing-database-objects"></a>Создание, изменение и удаление объектов баз данных
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Создание объектов SMO включает следующие этапы:  
  
1.  создание экземпляра объекта;  
  
2.  настройка свойств объекта;  
  
3.  создание экземпляров дочерних объектов;  
  
4.  настройка свойств дочерних объектов;  
  
5.  создание объекта.  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

 При создании в программе SMO экземпляров объектов SMO они не будут существовать в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , пока не будет вызван метод **Create** . Однако не обязательно запускать метод **Create** для каждого отдельного объекта. Если объект имеет набор дочерних объектов, метод **Create** необходимо вызвать только для родительского объекта. Например, при определении таблицы требуется, чтобы она содержала хотя бы один столбец. А столбец, в свою очередь, не может существовать без таблицы. Ниже представлена связь между таблицей и ее столбцами.  
  
 Метод <xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A> позволяет вносить изменения в объект. Несколько изменений объекта, например добавление дочерних объектов к одному из объектов коллекции или изменение значения свойства, объединяются в пакет и выполняются как одно изменение. Метод **Alter** уменьшает сетевой трафик и повышает общую производительность.  
  
 Инструкция **Drop** используется для удаления объекта и всех взаимозависимых дочерних объектов, которые требовались для первоначального создания объекта.  
  
## <a name="see-also"></a>См. также  
 [Объектная модель SMO](../../../relational-databases/server-management-objects-smo/smo-object-model.md)  
  
  
