---
title: 'Задача 9: Создание производной иерархии, с помощью диспетчера основных данных | Документация Майкрософт'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 22aba36efffe3b4e15d358e6077bb6b58e7aa328
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273590"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a>Задача 9. Создание производной иерархии с помощью диспетчера основных данных
  В этой задаче вы создадите производную иерархию с помощью диспетчера основных данных. Это производная иерархия наследуется от связей атрибутов на основе домена между **поставщика** и **состояние** сущностей.  
  
1.  Переключиться на главную страницу **диспетчера основных данных** , щелкнув **SQL Server 2012 Master Data Services** в верхней части страницы.  
  
2.  Нажмите кнопку **системное администрирование** в **административных задач** раздел.  
  
3.  Наведите указатель мыши **управление** в строке меню и нажмите кнопку **производные иерархии**.  
  
     ![Меню управления — выбрана производная иерархия](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "меню управления — выбрана производная иерархия")  
  
4.  Нажмите кнопку **Добавление производной иерархии (+)** на панели инструментов.  
  
     ![Добавьте кнопку в производная иерархия](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "производной иерархии кнопка \"Добавить\"")  
  
5.  Тип **SuppliersInState** для **имя производной иерархии**.  
  
6.  Нажмите кнопку **Сохранить** на панели инструментов.  
  
     ![Сохранить производную иерархию кнопку](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "сохранить производную иерархию кнопки")  
  
7.  Перетащите **поставщика** из **доступные уровни: SuppliersInState** для **текущие уровни: SuppliersInState**.  
  
     ![Доступные сущности и иерархии для текущего уровня](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "доступные сущности и иерархии для текущего уровня")  
  
8.  Перетащите **состояние** из **доступные уровни: SuppliersInState** для **текущие уровни: SuppliersInState**. На экране должны соответствовать **текущие уровни** как показано на следующем рисунке.  
  
     ![Текущие уровни и предварительный просмотр производной иерархии](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "текущие уровни и предварительный просмотр производной иерархии")  
  
9. В **предварительной версии** окне разверните **NY {Нью-Йорк}** и вы должны увидеть одного поставщика в этом состоянии, как показано на предыдущем рисунке.  
  
10. Переключиться на главную страницу **диспетчера основных данных** , щелкнув **SQL Server 2012 Master Data Services** в верхней части страницы.  
  
11. Нажмите кнопку **Браузер**.  
  
12. Наведите указатель мыши **иерархий** и нажмите кнопку **Derived: SuppliersInState**.  
  
     ![Иерархии — производный: SuppliersInState меню](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "иерархии - производные: SuppliersInState меню")  
  
13. Щелкните любой **состояние** узел в **представление в виде дерева** и вы увидите поставщиков в этом штате в области справа.  
  
     ![Производная иерархия в обозревателе](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "производная иерархия в обозревателе")  
  
## <a name="next-step"></a>Следующий шаг  
 [Урок 5. Автоматизация очистки данных и сопоставления с помощью служб SSIS](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  
