---
title: Перемещение элементов в решении | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- moving items
- solutions [SQL Server Management Studio], item relocation
- relocating items
ms.assetid: b40a24eb-f528-4e70-b26e-5eaf6e0ed1ed
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 217ad4a4d045798adaa7d430b0b91ba2eb3e8d7c
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67689807"
---
# <a name="move-items-in-a-solution"></a>Перемещение элементов в решении
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Элементами проекта в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] являются очереди, соединения и различные файлы. В обозревателе решений можно перемещать запросы и прочие файлы между проектами, но соединения перемещать нельзя.  
  
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
  
