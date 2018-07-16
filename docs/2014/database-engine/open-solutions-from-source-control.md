---
title: Открытие решения из системы управления версиями | Документация Майкрософт
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
- opening solutions
- solutions [SQL Server Management Studio], opening
ms.assetid: a96a1f0d-0183-4587-a3b0-4598309cbdd2
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0767df9d8ad010e17560b1f2b5e2e227d52a9f99
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285700"
---
# <a name="open-solutions-from-source-control"></a>Открытие решений из системы управления версиями
  Среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] можно использовать для открытия решений непосредственно из системы управления версиями. В этом случае среда Studio создает копию последней версии файлов решения в указанном месте.  
  
 Если копии решения на локальном диске не существует, то, прежде чем использовать среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] для извлечения решения или получения его файлов, следует открыть проект из системы управления версиями.  
  
> [!NOTE]  
>  Если локальная копия решения, открываемого из системы управления версиями, уже существует, следует подтвердить ее перезапись.  
  
### <a name="to-open-a-solution-from-source-control"></a>Открытие решения из системы управления версиями  
  
1.  На **файл** последовательно выберите пункты **системы управления версиями**и нажмите кнопку **открыть из системы управления версиями**.  
  
2.  Если будет выведено приглашение, войдите в [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.  
  
3.  В **Создание локального проекта из SourceSafe** диалоговое окно, выберите папку, содержащую решение, нужно открыть и нажмите кнопку **ОК**.  
  
4.  Если рабочая папка решения уже существует на локальном диске, **создайте новый проект в папке** поле изменится, отображая локальный каталог. Если для решения не существует рабочей папки, можно ввести вручную или выбрать имя каталога, в котором будет открыто решение.  
  
5.  В **открытое решение** диалоговом окне выберите файл решения и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Открытие проекта из системы управления версиями](../../2014/database-engine/open-projects-from-source-control.md)  
  
  
