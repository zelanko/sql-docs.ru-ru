---
title: "Перемещение элементов в решении | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- moving items
- solutions [SQL Server Management Studio], item relocation
- relocating items
ms.assetid: b40a24eb-f528-4e70-b26e-5eaf6e0ed1ed
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b0140646e92871aa5d3ab2acbb95b417ab38d28b
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="move-items-in-a-solution"></a>Перемещение элементов в решении
Элементами проекта в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] являются очереди, соединения и различные файлы. В обозревателе решений можно перемещать запросы и прочие файлы между проектами, но соединения перемещать нельзя.  
  
### <a name="to-move-items-in-solution-explorer"></a>Перемещение элемента в обозревателе решений  
  
1.  В обозревателе решений выберите элемент, который необходимо переместить.  
  
2.  В меню **Правка** выберите пункт **Вырезать**.  
  
3.  Выберите адресат в обозревателе решений.  
  
4.  В меню **Правка** выберите пункт **Вставить**.  
  
Запросы и прочие файлы также можно перемещать с помощью перетаскивания внутри обозревателя решений. Перетаскивание позволяет увидеть результат операции. После перемещения запросов из одного типа проектов в другой запросы могут рассматриваться в целевом проекте как прочие файлы.  
  
> [!NOTE]  
> При перемещении подключенного запроса соединение в целевой проект не перемещается. После перемещения запрос теряет соединение.  
  
## <a name="see-also"></a>См. также:  
[Обозреватель решений](../../ssms/solution/solution-explorer.md)  
[Копирование элементов в решении](../../ssms/solution/copy-items-in-a-solution.md)  
  

