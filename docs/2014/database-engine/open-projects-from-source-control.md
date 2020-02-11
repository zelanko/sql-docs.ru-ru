---
title: Открыть проекты из системы управления версиями | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62774958"
---
# <a name="open-projects-from-source-control"></a>Открытие проекта из системы управления версиями
  Для открытия проектов непосредственно из системы управления версиями следует использовать среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. В этом случае среда [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] извлекает последнюю версию проекта и копирует ее на локальный диск. Среда [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] при этом автоматически создает решение для проекта.  
  
 После открытия проекта из системы управления версиями можно извлекать и изменять файлы проекта.  
  
> [!NOTE]  
>  Приведенную ниже процедуру следует провести только один раз. После этого следует открыть проект, как и любой другой проект (щелкнув **файл**, **Открыть**, а затем **проект**).  
  
### <a name="to-open-a-project-from-source-control"></a>Открытие файла из системы управления версиями  
  
1.  В меню **файл** укажите пункт **система управления версиями**и выберите команду **Открыть из системы управления версиями**.  
  
2.  Если будет выведено приглашение, войдите в [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.  
  
3.  В диалоговом окне **Создание локального проекта из SourceSafe** откройте папку, содержащую проект, который нужно открыть.  
  
4.  Диалоговое окно **Создание нового проекта в папке** изменится, чтобы указать локальный каталог, в котором будет создан проект. Если вы хотите поместить проект в другой каталог, введите путь к каталогу или нажмите кнопку **Обзор** , чтобы найти каталог на локальном диске.  
  
5.  Убедитесь, что в **поле создать новый проект в папке**отображается правильная папка, и нажмите кнопку **ОК**.  
  
6.  В диалоговом окне **Открытие решения** выберите проект, который необходимо открыть, и нажмите кнопку **Открыть**.  
  
## <a name="see-also"></a>См. также:  
 [Открытие решений и проектов из системы управления версиями](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)   
 [Открытие решений из системы управления версиями](../../2014/database-engine/open-solutions-from-source-control.md)  
  
  
