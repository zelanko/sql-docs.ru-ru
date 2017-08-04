---
title: "Отладка сценария, установив точки останова в задаче «скрипт» и компоненте скрипта | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- breakpoints [Integration Services]
- scripts [Integration Services], breakpoints
ms.assetid: 6c03464f-3f7d-4882-b7f8-8e396f8e2944
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 96815b337311c4ba8d16e10c25891c728e7a0c74
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component"></a>Отладка скрипта с помощью точек останова в задаче и компоненте «Скрипт»
  Эта процедура описывает способ создания точки останова в скриптах, используемых задачей «Скрипт» и компонентом «Скрипт».  
  
 После задания точек останова в скрипте, **установка точек останова — \<имя объекта >** диалоговом окне приводится список точек останова вместе со встроенными точками.  
  
> [!IMPORTANT]  
>  В некоторых случаях точки останова из задачи «Скрипт» и компонента скрипта пропускаются. Дополнительные сведения см. в разделе **отладка задачи «скрипт»** статьи [кодировании и отладке задачи «скрипт»](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md) и **отладка компонента скрипта** статьи [кодировании и отладке компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="to-set-a-breakpoint-in-script"></a>Задание точки останова в скрипте  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Дважды щелкните пакет, содержащий скрипт, в котором нужно создать точки останова.  
  
3.  Чтобы открыть задачу «скрипт», щелкните **поток управления** вкладку, а затем дважды щелкните задачу «скрипт».  
  
4.  Чтобы открыть компонент скрипта, щелкните **потока данных** вкладку, а затем дважды щелкните компонент скрипта.  
  
5.  Нажмите кнопку **сценарий** и нажмите кнопку **изменить скрипт**.  
  
6.  В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] средств для приложений (VSTA), найдите строку скрипта, на котором требуется установить точку останова, щелкните эту строку правой кнопкой мыши **останова**, а затем нажмите кнопку **вставить точку останова**.  
  
     Значок точки останова появится на строке с кодом.  
  
7.  В меню **Файл** выберите пункт **Выход**.  
  
8.  Нажмите кнопку **ОК**.  
  
9. Чтобы сохранить пакеты, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
  
