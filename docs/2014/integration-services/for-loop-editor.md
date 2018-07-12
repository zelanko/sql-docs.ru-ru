---
title: Редактор циклов по элементам | Документация Майкрософт
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.forloopcontainer.f1
ms.assetid: c4db9df6-d2f4-44da-9f4d-628893e86956
caps.latest.revision: 26
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: af80869fbba015492b469af030d5cc297e7127e6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37205824"
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
  
 **Название**  
 Содержит уникальное имя для контейнера «цикл по элементам». Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена объектов в пределах пакета должны быть уникальными.  
  
 **Описание**  
 Описание контейнера «цикл по элементам».  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Страница «выражения»](expressions/expressions-page.md)   
 [Контейнер "Цикл по каждому элементу"](control-flow/foreach-loop-container.md)   
 [Настройка контейнера "цикл по элементам"](../../2014/integration-services/configure-a-for-loop-container.md)  
  
  
