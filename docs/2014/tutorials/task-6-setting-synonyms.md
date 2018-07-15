---
title: 'Задача 6: Задание синонимов | Документация Майкрософт'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b7d35ee9-d1c9-41d9-bbc5-0ca7db93e54d
caps.latest.revision: 8
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 11be818da421f02ec07b13c632c4fcda87652442
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323874"
---
# <a name="task-6-setting-synonyms"></a>Задача 6. Задание синонимов
  В этой задаче вы зададите два значения, **USA** и **United States**, домена **Страна** как синонимы, при этом **United States** будет начальным значением. Поскольку параметр **Использовать начальные значения** был выбран при создании домена **Страна** , все значения **USA** для домена **Страна** будут выводиться как **United States** (при этом «United States» — начальное значение). Дополнительные сведения см. в разделе [Изменение значений домена](http://msdn.microsoft.com/library/hh510408.aspx) .  
  
1.  Выберите **Страна** в списке доменов.  
  
2.  Перейдите на вкладку **Значения домена** .  
  
3.  Нажмите кнопку **Добавить новое значение домена** на панели инструментов.  
  
4.  Введите **USA** и нажмите клавишу **ВВОД**.  
  
5.  Выберите **United States** и **USA** с помощью клавиш CTRL или SHIFT, щелкните правой кнопкой выделенные элементы и выберите пункт **Установить как синонимы**. Службы DQS сгруппируют эти значения и назначат одно из значений в качестве ведущего, которым будут заменяться другие.  
  
     ![Задать как синонимы меню](../../2014/tutorials/media/et-settingsynonyms-01.jpg "задать как синонимы меню")  
  
6.  Обратите внимание, что значение **United States** задано как начальное. Если вы хотите, чтобы «USA» было начальным значением, щелкните «USA» правой кнопкой мыши и выберите параметр **Установить в качестве ведущего** . В этом учебнике мы будем использовать значение **United States** как начальное.  
  
     ![США и США как синонимы](../../2014/tutorials/media/et-settingsynonyms-02.jpg "США и США как синонимы")  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 7. Создание составного домена](../../2014/tutorials/task-7-creating-a-composite-domain.md)  
  
  
