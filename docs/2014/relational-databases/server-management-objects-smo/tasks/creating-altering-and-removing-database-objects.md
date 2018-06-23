---
title: Работа с объектами базы данных | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- database objects [SMO]
- objects [SMO]
ms.assetid: 702fd63d-8734-4a02-872e-aecfb037c787
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1d0291713da7d8caccf5461eaf92de21207b0bd9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097028"
---
# <a name="working-with-database-objects"></a>Работа с объектами базы данных
  Создание объектов SMO включает следующие этапы:  
  
1.  создание экземпляра объекта;  
  
2.  настройка свойств объекта;  
  
3.  создание экземпляров дочерних объектов;  
  
4.  настройка свойств дочерних объектов;  
  
5.  создание объекта.  
  
 При создании в приложении SMO экземпляров объектов SMO они не будут существовать в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], пока не будет вызван метод `Create`. Однако не обязательно запускать метод `Create` для каждого отдельного объекта. Если объект имеет набор дочерних объектов, метод `Create` необходимо вызвать только для родительского объекта. Например, при определении таблицы требуется, чтобы она содержала хотя бы один столбец. А столбец, в свою очередь, не может существовать без таблицы. Ниже представлена связь между таблицей и ее столбцами.  
  
 Метод <xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A> позволяет вносить изменения в объект. Несколько изменений объекта, например добавление дочерних объектов к одному из объектов коллекции или изменение значения свойства, объединяются в пакет и выполняются как одно изменение. Метод `Alter` уменьшает сетевой трафик и повышает общую производительность.  
  
 Инструкция `Drop` используется для удаления объекта и всех взаимозависимых дочерних объектов, которые требовались для первоначального создания объекта.  
  
## <a name="see-also"></a>См. также  
 [Объектная модель SMO](../smo-object-model.md)  
  
  