---
title: Редактор циклов по элементам | Документация Майкрософт
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.forloopcontainer.f1
ms.assetid: c4db9df6-d2f4-44da-9f4d-628893e86956
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: da5e5c2a748a2bd38d0337b70e9d2a3da312df43
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894485"
---
# <a name="for-loop-editor"></a>Редактор циклов по элементам
  На странице **Цикл по элементам** диалогового окна **Редактор циклов по элементам** можно настроить цикл, в котором рабочий процесс будет повторяться до тех пор, пока заданное условие не примет значение False.  
  
 Дополнительные сведения о контейнере «цикл по элементам» и его использовании в пакетах см. в разделе [For Loop Container](control-flow/for-loop-container.md).  
  
## <a name="options"></a>Параметры  
 **InitExpression**  
 Необязательный параметр. Выражение для инициализации значений, используемых в цикле.  
  
 **EvalExpression**  
 Выражение, с помощью которого определяется условие завершения или продолжения цикла.  
  
 **AssignExpression**  
 Необязательный параметр. Выражение, с помощью которого каждый раз при повторении цикла изменяется условие.  
  
 **Name**  
 Содержит уникальное имя для контейнера «цикл по элементам». Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена объектов в пределах пакета должны быть уникальными.  
  
 **Описание**  
 Описание контейнера «цикл по элементам».  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Страница «Выражения»](expressions/expressions-page.md)   
 [Контейнер "Цикл по каждому элементу"](control-flow/foreach-loop-container.md)   
 [Настройка контейнера "цикл по элементам"](../../2014/integration-services/configure-a-for-loop-container.md)  
  
  
