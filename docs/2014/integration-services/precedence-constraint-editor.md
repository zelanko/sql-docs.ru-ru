---
title: Редактор ограничений очередностью | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.precedenceconstraint.f1
helpviewer_keywords:
- Precedence Constraint Editor dialog box
ms.assetid: b10d4330-6e35-4037-b309-ef56efcd60c5
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1753bb3469b5909bfd74728eca1f3a49fd4f2ba9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095234"
---
# <a name="precedence-constraint-editor"></a>Редактор управления очередностью
  Диалоговое окно **Редактор ограничений очередностью** используется для настройки ограничений очередностью.  
  
## <a name="options"></a>Параметры  
 **Вычислительная операция**  
 Определяет вычислительную операцию, которую использует ограничение очередностью. Операциями могут быть: **Ограничение**, **Выражение**, **Выражение и ограничение**и **Выражение или ограничение**.  
  
 **Value**  
 Укажите ограничение по значению: **Успешно**, **Сбой**или **Завершение**.  
  
> [!NOTE]  
>  Строка элементов управления очередностью имеет зеленый цвет для значения **Успех**, синий — для значения **Завершение**и выделяется для значения **Неудача**.  
  
 **Выражение**  
 При использовании действий **Выражение**, **Выражение и ограничение**или **Выражение или ограничение**введите выражение или запустите построитель выражений для создания выражения. Выражение должно иметь логическое значение.  
  
 **Тест**  
 Проверка выражения.  
  
 **Логическое И**  
 Выберите, чтобы указать, что несколько ограничений очередности в одном исполняемом объекте должны учитываться вместе. Все ограничения должны иметь значение `True`.  
  
> [!NOTE]  
>  Этот тип элементов управления очередностью имеет вид сплошной зеленой или синей линии либо выделяется.  
  
 **Логическое ИЛИ**  
 Выберите, чтобы указать, что несколько ограничений очередности в одном исполняемом объекте должны учитываться вместе. По крайней мере одно ограничение должно иметь значение `True`.  
  
> [!NOTE]  
>  Этот тип элементов управления очередностью имеет вид пунктирной зеленой или синей линии либо выделяется.  
  
## <a name="see-also"></a>См. также  
 [Управление очередностью](control-flow/precedence-constraints.md)   
 [Задачи служб Integration Services](control-flow/integration-services-tasks.md)   
 [Контейнеры служб Integration Services](control-flow/integration-services-containers.md)   
 [Выражения служб Integration Services (SSIS)](expressions/integration-services-ssis-expressions.md)  
  
  