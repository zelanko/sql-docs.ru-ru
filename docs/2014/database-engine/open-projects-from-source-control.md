---
title: Открывать проекты из системы управления версиями | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], opening
- opening projects
ms.assetid: 942f93a3-e264-4ec4-ba72-a28e0509a527
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ec14f86b283fa8ccbc037feec4a8a54983126403
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62774958"
---
# <a name="open-projects-from-source-control"></a>Открытие проекта из системы управления версиями
  Для открытия проектов непосредственно из системы управления версиями следует использовать среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. В этом случае среда [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] извлекает последнюю версию проекта и копирует ее на локальный диск. Среда [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] при этом автоматически создает решение для проекта.  
  
 После открытия проекта из системы управления версиями можно извлекать и изменять файлы проекта.  
  
> [!NOTE]  
>  Приведенную ниже процедуру следует провести только один раз. После этого следует открыть проект как любой другой проект (, щелкнув **файл**, **откройте**, а затем **проекта**).  
  
### <a name="to-open-a-project-from-source-control"></a>Открытие файла из системы управления версиями  
  
1.  На **файл** последовательно выберите пункты **системы управления версиями**и нажмите кнопку **открыть из системы управления версиями**.  
  
2.  Если будет выведено приглашение, войдите в [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.  
  
3.  В **Создание локального проекта из SourceSafe** диалоговом окне откройте папку, содержащую требуемый проект.  
  
4.  **Создайте новый проект в папке** поле изменится, отображая локальный каталог, в котором будет создан проект. Если вы хотите разместить проект в другом каталоге, введите путь каталога или воспользуйтесь **Обзор** кнопку, чтобы найти каталог на локальном диске.  
  
5.  В **создайте новый проект в соответствующем окне папки**, убедитесь, что отображается правильная папка и нажмите кнопку **ОК**.  
  
6.  В **открыть решение** диалоговое окно, выберите проект, необходимо открыть и нажмите кнопку **откройте**.  
  
## <a name="see-also"></a>См. также  
 [Открытие решений и проектов из системы управления версиями](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)   
 [Открытие решений из системы управления версиями](../../2014/database-engine/open-solutions-from-source-control.md)  
  
  
