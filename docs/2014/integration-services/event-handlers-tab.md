---
title: Вкладка «обработчики событий» | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.eventhandlerwindow.f1
ms.assetid: 94fc8916-8032-490c-b9d5-ded8b6217e49
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 49b6145f29fac5088d44e6e82f6dcd3eb491556a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095480"
---
# <a name="event-handlers-tab"></a>Вкладка «Обработчики событий»
  Используйте вкладку **Обработчики событий** конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] , чтобы сформировать поток управления в пакете служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Обработчик события запускается в ответ на событие, инициированное либо пакетом, либо задачей или контейнером в пакете.  
  
## <a name="options"></a>Параметры  
 **Исполняемый объект**  
 Выберите исполняемый объект, для которого необходимо создать обработчик события. Исполняемый объект может быть либо пакетом, либо задачей или контейнером в пакете.  
  
 **Обработчик событий**  
 Выберите тип обработчика события. Создайте обработчик события, перетащив элементы из **Области элементов**.  
  
 **Удаление**  
 Выберите обработчик события и удалите его из пакета, нажав кнопку **Удалить**.  
  
 **Щелкните здесь, чтобы создать \<имя обработчика события > для исполняемого файла \<имя исполняемого файла >**  
 Нажмите, чтобы создать обработчик события.  
  
 Создайте поток управления, перетащив графические объекты, которые представляют задачи и контейнеры служб [!INCLUDE[ssIS](../includes/ssis-md.md)] , из **Области элементов** в область конструктора вкладки **Обработчики событий** , соединяя затем объекты при помощи объектов управления очередностью, чтобы определить последовательность их запуска.  
  
 Кроме того, чтобы добавить заметки, щелкните правой кнопкой мыши в области конструктора и выберите из меню команду **Добавить заметку**.  
  
## <a name="see-also"></a>См. также  
 [Обработчики событий в службах Integration Services (SSIS)](integration-services-ssis-event-handlers.md)   
 [Поток управления](control-flow/control-flow.md)   
 [Конструктор служб SSIS](ssis-designer.md)   
 [Службы Integration Services &#40;SSIS&#41; обработчики событий](integration-services-ssis-event-handlers.md)  
  
  