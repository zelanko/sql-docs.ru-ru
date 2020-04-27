---
title: Использование выражения в ограничении очередностью | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- precedence constraints [Integration Services], adding expressions
- expressions [Integration Services], adding
ms.assetid: 601038bb-3b17-42ac-b09d-5b3a82fb6564
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 672d9c363f64037f5f40f51fc7c6cb1c4c3bc674
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054749"
---
# <a name="use-an-expression-in-a-precedence-constraint"></a>Использование выражения в элементах управлении очередностью
  Эта процедура описывает добавление выражений к объекту управления очередностью с помощью диалогового окна **Редактор управления очередностью** . Перед добавлением выражения к управлению очередностью пакет должен содержать по меньшей мере два исполняемых объекта (задачи или контейнера), которые должны быть соединены объектом управления очередностью.  
  
### <a name="to-add-an-expression-to-a-precedence-constraint"></a>Добавление выражения к элементу управления очередностью  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **Поток управления** .  
  
4.  В области конструктора на вкладке **Поток управления** дважды щелкните объект управления очередностью. Открывается **Редактор управления очередностью** .  
  
5.  Выберите пункт **Выражение**, **Выражение и ограничение**или **Выражение или ограничение** в списке **Вычислительная операция** .  
  
6.  Введите выражение в текстовое поле **Выражение** или запустите построитель выражений, чтобы создать выражение.  
  
7.  Чтобы проверить правильность синтаксиса выражения, нажмите кнопку **Проверить**.  
  
8.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также  
 [Управление очередностью](control-flow/precedence-constraints.md)   
 [Подключение задач и контейнеров с помощью управления очередностью по умолчанию](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [Установка значения управления очередностью с помощью контекстного меню](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [Задание свойств управления очередностью](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)   
 [Выражения служб Integration Services (SSIS)](expressions/integration-services-ssis-expressions.md)  
  
  
