---
title: Перемещение элементов в решении | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- moving items
- solutions [SQL Server Management Studio], item relocation
- relocating items
ms.assetid: b40a24eb-f528-4e70-b26e-5eaf6e0ed1ed
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 27bbc90e2d4504fb9b5a4de0d876115a3997a96b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280700"
---
# <a name="move-items-in-a-solution"></a>Перемещение элементов в решении
  Элементами проекта в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] являются очереди, соединения и различные файлы. В обозревателе решений можно перемещать запросы и прочие файлы между проектами, но соединения перемещать нельзя.  
  
### <a name="to-move-items-in-solution-explorer"></a>Перемещение элемента в обозревателе решений  
  
1.  В обозревателе решений выберите элемент, который необходимо переместить.  
  
2.  В меню **Правка** выберите пункт **Вырезать**.  
  
3.  Выберите адресат в обозревателе решений.  
  
4.  В меню **Правка** выберите пункт **Вставить**.  
  
 Запросы и прочие файлы также можно перемещать с помощью перетаскивания внутри обозревателя решений. Перетаскивание позволяет увидеть результат операции. После перемещения запросов из одного типа проектов в другой запросы могут рассматриваться в целевом проекте как прочие файлы.  
  
> [!NOTE]  
>  При перемещении подключенного запроса соединение в целевой проект не перемещается. После перемещения запрос теряет соединение.  
  
## <a name="see-also"></a>См. также  
 [Обозреватель решений](solution-explorer.md)   
 [Копирование элементов в решении](copy-items-in-a-solution.md)  
  
  
