---
title: Вкладка "обработчики событий" | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.eventhandlerwindow.f1
ms.assetid: 94fc8916-8032-490c-b9d5-ded8b6217e49
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 4bd7e159a148b134d744481a76ac910af572c0c2
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969414"
---
# <a name="event-handlers-tab"></a>Вкладка «Обработчики событий»
  Используйте вкладку **Обработчики событий** конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] , чтобы сформировать поток управления в пакете служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Обработчик события запускается в ответ на событие, инициированное либо пакетом, либо задачей или контейнером в пакете.  
  
## <a name="options"></a>Варианты  
 **Исполняемый объект**  
 Выберите исполняемый объект, для которого необходимо создать обработчик события. Исполняемый объект может быть либо пакетом, либо задачей или контейнером в пакете.  
  
 **Обработчик событий**  
 Выберите тип обработчика события. Создайте обработчик события, перетащив элементы из **Области элементов**.  
  
 **Удаление**  
 Выберите обработчик события и удалите его из пакета, нажав кнопку **Удалить**.  
  
 **Щелкните здесь, чтобы создать \<event handler name> для исполняемого файла\<executable name>**  
 Нажмите, чтобы создать обработчик события.  
  
 Создайте поток управления, перетащив графические объекты, которые представляют задачи и контейнеры служб [!INCLUDE[ssIS](../includes/ssis-md.md)] , из **Области элементов** в область конструктора вкладки **Обработчики событий** , соединяя затем объекты при помощи объектов управления очередностью, чтобы определить последовательность их запуска.  
  
 Кроме того, чтобы добавить заметки, щелкните правой кнопкой мыши в области конструктора и выберите из меню команду **Добавить заметку**.  
  
## <a name="see-also"></a>См. также:  
 [Integration Services &#40;служб SSIS&#41; обработчики событий](integration-services-ssis-event-handlers.md)   
 [Поток управления](control-flow/control-flow.md)   
 [Конструктор служб SSIS](ssis-designer.md)   
 [Обработчики событий в службах Integration Services (SSIS)](integration-services-ssis-event-handlers.md)  
  
  
