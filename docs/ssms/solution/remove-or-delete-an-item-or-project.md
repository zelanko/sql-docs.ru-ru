---
title: Перемещение или удаление элемента или проекта | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting project items
- projects [SQL Server Management Studio], item removal
- removing project items
ms.assetid: 3fd92434-70f5-466e-bef0-7e0fd73ddb1c
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4300cdd7ae29fe33f1843f5ecc6e7e389d982e58
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65102939"
---
# <a name="remove-or-delete-an-item-or-project"></a>Перемещение или удаление элемента или проекта
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
  
Проект можно удалить окончательно, но для этого сначала необходимо удалить все ссылки на проект из решений среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , а затем с помощью проводника [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows окончательно удалить связанные с проектом файлы из хранилища.  
  
#### <a name="to-delete-a-project"></a>Удаление проекта  
  
1.  В обозревателе решений исключите из решения проект, который требуется удалить окончательно.  
  
2.  В проводнике Windows найдите и выделите файлы, связанные с проектом или элементом, который требуется удалить.  
  
3.  В меню **Файл** выберите пункт **Удалить**.  
  
## <a name="see-also"></a>См. также:  
[Обозреватель решений](../../ssms/solution/solution-explorer.md)  
[Добавление в проект новые элементы](../../ssms/solution/add-new-items-to-a-project.md)  
[Добавление существующих элементов в проект](../../ssms/solution/add-existing-items-to-a-project.md)  
  
