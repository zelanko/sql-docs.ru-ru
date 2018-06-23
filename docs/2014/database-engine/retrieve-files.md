---
title: Получение файлов | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- version control services [SQL Server], file retrieval
- file retrieval [SQL Server]
- retrieving files
ms.assetid: 37b74426-e262-43b2-a81f-79b1fd1a36ec
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f1b53eb99abc77e809bd7aaac30f8f218cd4ee03
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096219"
---
# <a name="retrieve-files"></a>Получение файлов
  После открытия проекта, контролируемого системой управления версиями, среда [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] позволяет загрузить локальную копию файлов проекта из хранилища системы управления версиями в локальный каталог проекта.  
  
 Встроенную систему управления версиями можно использовать для получения файлов следующими способами.  
  
-   **Получить последнюю версию (рекурсивно)** команды  
  
     Получение последней возвращенной версии выбранных файлов. Если выбрано решение или проект, по этой команде можно получить последнюю версию всех файлов решения или проекта.  
  
-   **Получить** команды  
  
     Отображает **получить** dialog box, в котором можно использовать для получения последней версии выбранного файла или для получения набора файлов выбранного решения или проекта.  
  
### <a name="to-retrieve-the-latest-version-of-all-the-files-in-a-project"></a>Получение последней версии всех файлов проекта  
  
1.  Выберите проект в обозревателе решений.  
  
2.  На **файл** последовательно выберите пункты **системы управления версиями**, а затем нажмите кнопку **получить последнюю версию (рекурсивно)**.  
  
 Последние версии файлов в проекте извлекаются в расположение проекта на локальном диске.  
  
#### <a name="to-retrieve-only-certain-files-in-a-project"></a>Получение отдельных файлов проекта  
  
1.  В обозревателе решений выберите элемент, который необходимо получить.  
  
2.  На **файл** последовательно выберите пункты **системы управления версиями**, а затем нажмите кнопку **получить**.  
  
3.  В **получить** диалоговое окно, нажмите кнопку **ОК**. Если решение или проект выбрано в обозревателе решений, можно снять флажки, расположенные рядом с элементами, которые не нужно получать.  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно &#40;система управления версиями&#41;](../../2014/database-engine/get-dialog-box-source-control.md)   
 [Задание и получение сведений о версии](../../2014/database-engine/set-and-retrieve-version-information.md)   
 [Просмотр журнала проекта](../../2014/database-engine/view-project-history.md)   
 [Просмотр состояния файла](../../2014/database-engine/view-file-status.md)  
  
  