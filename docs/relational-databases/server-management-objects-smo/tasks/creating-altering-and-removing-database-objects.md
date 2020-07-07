---
title: Работа с объектами базы данных
ms.custom: seo-dt-2019
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
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 624de23d309aac6f453054c2bf7a7a10b4a478ec
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86001358"
---
# <a name="creating-altering-and-removing-database-objects"></a>Создание, изменение и удаление объектов баз данных
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

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
 [Объектная модель SMO](../../../relational-databases/server-management-objects-smo/smo-object-model.md)  
  
  
