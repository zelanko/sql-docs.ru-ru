---
title: Настройка контейнера «цикл по каждому элементу» | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: b9cd7ea7-b198-4a35-8b16-6acf09611ca5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fe51deb631f0c3d794bdce3f05af61b5e030d5e3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66060830"
---
# <a name="configure-a-for-loop-container"></a>Настройка контейнера «цикл по элементам»
  В процедуре описывается, как настроить контейнер «цикл по элементам» с помощью диалогового окна **Редактор циклов по элементам** .  
  
 Пример контейнера цикла «по элементам» см. в статье [Циклы SSIS, не завершающиеся сбоями](https://go.microsoft.com/fwlink/?LinkId=240295) на сайте bimonkey.com.  
  
### <a name="to-configure-the-for-loop-container"></a>Настройка контейнера «цикл по элементам»  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]дважды щелкните контейнер "цикл по элементам", чтобы открыть **Редактор циклов по элементам**.  
  
2.  При необходимости измените имя и описание контейнера «цикл по элементам».  
  
3.  При необходимости введите выражение инициализации в текстовое поле **InitExpression** .  
  
4.  Введите выражение в текстовое поле **EvalExpression** .  
  
    > [!NOTE]  
    >  Выражение должно иметь логическое значение. Если значением этого выражения будет `false`, выполнение цикла останавливается.  
  
5.  При необходимости введите выражение присвоения в текстовое поле **AssignExpression** .  
  
6.  При необходимости щелкните **Выражения** и на странице **Выражения** создайте выражения свойств для свойств контейнера «цикл по элементам». Дополнительные сведения см. в разделе [Добавление или изменение выражение свойства](expressions/add-or-change-a-property-expression.md).  
  
7.  Щелкните **ОК** , чтобы закрыть **Редактор циклов For**.  
  
## <a name="see-also"></a>См. также:  
 [Контейнер «цикл по каждому»](control-flow/for-loop-container.md)   
 [Выражения&#41; Integration Services &#40;SSIS](expressions/integration-services-ssis-expressions.md)   
 [Использование выражений свойств в пакетах](expressions/use-property-expressions-in-packages.md)  
  
  
