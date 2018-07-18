---
title: Выполнение отладки пакета путем установки точек останова для задачи или контейнера | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], breakpoints
- breakpoints [Integration Services]
- tasks [Integration Services], breakpoints
ms.assetid: e7fa106a-2221-403a-bb74-efc9f12bb450
caps.latest.revision: 33
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b063089105af1de7656387be8cc12639498e7c37
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308114"
---
# <a name="debug-a-package-by-setting-breakpoints-on-a-task-or-a-container"></a>Выполнение отладки пакета путем установки точек останова для задачи или контейнера
  Эта процедура описывает, как установить точки останова в пакете, задаче, контейнерах «цикл по элементам», «цикл по каждому элементу» и контейнере последовательности.  
  
### <a name="to-set-breakpoints-in-a-package-a-task-or-a-container"></a>Установка точки останова в пакете, задаче или контейнере  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Дважды щелкните пакет, для которого следует установить точки останова.  
  
3.  В конструкторе служб SSIS сделайте следующее.  
  
    -   Чтобы установить точки останова в объекте пакета, перейдите на вкладку **Поток управления** , поместите курсор где-либо на заднем плане области конструктора, щелкните правой кнопкой мыши и выберите пункт **Изменить точки останова**.  
  
    -   Чтобы установить точки останова в потоке управления пакета, перейдите на вкладку **Поток управления** , правой кнопкой мыши щелкните задачу, контейнер "цикл по элементам", "цикл по каждому элементу" или контейнер последовательности и выберите пункт **Изменить точки останова**.  
  
    -   Чтобы установить точки останова в обработчике события, перейдите на вкладку **Обработчик события** , щелкните правой кнопкой мыши задачу, контейнер "цикл по элементам", "цикл по каждому элементу" или контейнер последовательности и выберите пункт **Изменить точки останова**.  
  
4.  В диалоговом окне **Задание точек останова \<имя контейнера>** выберите точки останова для включения.  
  
5.  При необходимости измените тип счетчика попаданий и значение числа попаданий для каждой точки останова.  
  
6.  Чтобы сохранить пакеты, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также  
 [Средства устранения неполадок для разработки пакетов](troubleshooting/troubleshooting-tools-for-package-development.md)   
 [Отладка скрипта с помощью точек останова в задаче «скрипт» и компоненте скрипта](data-flow/transformations/script-component.md)   
 [Кодирование и отладка задачи «скрипт»](control-flow/script-task.md)   
 [Кодирование и отладка компонента скрипта](extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  
