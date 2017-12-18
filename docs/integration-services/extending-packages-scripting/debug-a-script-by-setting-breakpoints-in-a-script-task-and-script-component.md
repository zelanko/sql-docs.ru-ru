---
title: "Отладка скрипта с помощью точек останова в задаче и компоненте \"Скрипт\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- breakpoints [Integration Services]
- scripts [Integration Services], breakpoints
ms.assetid: 6c03464f-3f7d-4882-b7f8-8e396f8e2944
caps.latest.revision: "33"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f16bd3fc90efc5c366660f388c5c719ed70185ac
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component"></a>Отладка скрипта с помощью точек останова в задаче и компоненте «Скрипт»
  Эта процедура описывает способ создания точки останова в скриптах, используемых задачей «Скрипт» и компонентом «Скрипт».  
  
 После задания точек останова в скрипте в диалоговом окне **Установка точек останова — \<имя объекта>** будет приведен список этих точек останова вместе со встроенными точками останова.  
  
> [!IMPORTANT]  
>  В некоторых случаях точки останова из задачи «Скрипт» и компонента скрипта пропускаются. Дополнительные сведения об отладке задачи и компонента "Скрипт" см. в пунктах **Отладка задачи "Скрипт"** раздела [Кодирование и отладка задачи "Скрипт"](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md), а также **Отладка компонента скрипта** раздела [Кодирование и отладка компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="to-set-a-breakpoint-in-script"></a>Задание точки останова в скрипте  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Дважды щелкните пакет, содержащий скрипт, в котором нужно создать точки останова.  
  
3.  Чтобы открыть задачу "Скрипт", следует перейти на вкладку **Поток управления** и дважды щелкнуть задачу "Скрипт".  
  
4.  Чтобы открыть компонент "Скрипт", следует перейти на вкладку **Поток данных** и дважды щелкнуть компонент "Скрипт".  
  
5.  Щелкните **Скрипт**, затем нажмите кнопку **Изменить скрипт**.  
  
6.  В среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] набор средств Visual Studio Tools для работы с приложениями (VSTA) найдите строку скрипта, на которой следует установить точку останова, щелкните правой кнопкой мыши, выберите **Точка останова**, а затем **Вставить точку останова**.  
  
     Значок точки останова появится на строке с кодом.  
  
7.  В меню **Файл** выберите пункт **Выход**.  
  
8.  Нажмите кнопку **ОК**.  
  
9. Чтобы сохранить пакеты, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
  
