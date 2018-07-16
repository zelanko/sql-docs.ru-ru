---
title: Перемещение или удаление элемента или проекта | Документация Майкрософт
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
- deleting project items
- projects [SQL Server Management Studio], item removal
- removing project items
ms.assetid: 3fd92434-70f5-466e-bef0-7e0fd73ddb1c
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10a5ee3209b6101deda62171c1f0f57bebf23121
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246224"
---
# <a name="remove-or-delete-an-item-or-project"></a>Перемещение или удаление элемента или проекта
  Элементами проекта в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] являются очереди, соединения и различные файлы. Запросы и прочие файлы проектов можно удалять из решения без удаления соответствующих им файлов из хранилища. Переместите проект или элемент, если он не нужен в текущем решении, но его надо использовать в другом решении.  
  
### <a name="to-remove-a-project-item"></a>Исключение элемента проекта  
  
1.  В обозревателе решений выберите элемент проекта, который требуется исключить.  
  
2.  В меню **Правка** выберите пункт **Удалить**.  
  
3.  В диалоговом окне подтверждения нажмите кнопку **Удалить** для исключения элемента из проекта.  
  
 Исключенный элемент продолжает существовать в файловой системе. Поэтому исключенный элемент можно вновь добавить в исходное или другое решение.  
  
#### <a name="to-remove-a-project"></a>Исключение проекта  
  
1.  В обозревателе решений выберите проект, который требуется исключить.  
  
2.  В меню **Правка** выберите пункт **Удалить**.  
  
3.  В диалоговом окне подтверждения нажмите кнопку **ОК**для исключения проекта из решения.  
  
 Проект можно удалить окончательно, но для этого сначала необходимо удалить все ссылки на проект из решений среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , а затем с помощью проводника [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows окончательно удалить связанные с проектом файлы из хранилища.  
  
#### <a name="to-delete-a-project"></a>Удаление проекта  
  
1.  В обозревателе решений исключите из решения проект, который требуется удалить окончательно.  
  
2.  В проводнике Windows найдите и выделите файлы, связанные с проектом или элементом, который требуется удалить.  
  
3.  В меню **Файл** выберите пункт **Удалить**.  
  
## <a name="see-also"></a>См. также  
 [Обозреватель решений](solution-explorer.md)   
 [Добавление новых элементов в проект](add-new-items-to-a-project.md)   
 [Добавление существующих элементов в проект](add-existing-items-to-a-project.md)  
  
  
