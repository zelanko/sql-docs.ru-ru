---
title: Перемещение или удаление элемента или проекта | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-solutions
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deleting project items
- projects [SQL Server Management Studio], item removal
- removing project items
ms.assetid: 3fd92434-70f5-466e-bef0-7e0fd73ddb1c
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 96e5484ed59b0852f0099602b5a4e3ff359d1b6f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="remove-or-delete-an-item-or-project"></a>Перемещение или удаление элемента или проекта
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Элементами проекта в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] являются очереди, соединения и различные файлы. Запросы и прочие файлы проектов можно удалять из решения без удаления соответствующих им файлов из хранилища. Переместите проект или элемент, если он не нужен в текущем решении, но его надо использовать в другом решении.  
  
### <a name="to-remove-a-project-item"></a>Исключение элемента проекта  
  
1.  В обозревателе решений выберите элемент проекта, который требуется исключить.  
  
2.  В меню **Правка** выберите пункт **Удалить**.  
  
3.  В диалоговом окне подтверждения нажмите кнопку **Удалить** для исключения элемента из проекта.  
  
Исключенный элемент продолжает существовать в файловой системе. Поэтому исключенный элемент можно вновь добавить в исходное или другое решение.  
  
#### <a name="to-remove-a-project"></a>Исключение проекта  
  
1.  В обозревателе решений выберите проект, который требуется исключить.  
  
2.  В меню **Правка** выберите пункт **Удалить**.  
  
3.  В диалоговом окне подтверждения нажмите кнопку **ОК**для исключения проекта из решения.  
  
Проект можно удалить окончательно, но для этого сначала необходимо удалить все ссылки на проект из решений среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] , а затем с помощью проводника [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows окончательно удалить связанные с проектом файлы из хранилища.  
  
#### <a name="to-delete-a-project"></a>Удаление проекта  
  
1.  В обозревателе решений исключите из решения проект, который требуется удалить окончательно.  
  
2.  В проводнике Windows найдите и выделите файлы, связанные с проектом или элементом, который требуется удалить.  
  
3.  В меню **Файл** выберите пункт **Удалить**.  
  
## <a name="see-also"></a>См. также:  
[Обозреватель решений](../../ssms/solution/solution-explorer.md)  
[Добавление в проект новые элементы](../../ssms/solution/add-new-items-to-a-project.md)  
[Добавление существующих элементов в проект](../../ssms/solution/add-existing-items-to-a-project.md)  
  
