---
title: 'Задача 9: Создание производной иерархии, с помощью диспетчера основных данных | Документы Microsoft'
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
ms.topic: article
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 35584d33afac7a2a8f74abd013288a974cade512
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195279"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a>Задача 9. Создание производной иерархии с помощью диспетчера основных данных
  В этой задаче вы создадите производную иерархию с помощью диспетчера основных данных. Это производная иерархия наследуется от связей атрибутов на основе домена между **Supplier** и **состояние** сущностей.  
  
1.  Переключитесь на главной странице **диспетчера основных данных** , щелкнув **SQL Server 2012 Master Data Services** в верхней части страницы.  
  
2.  Нажмите кнопку **системное администрирование** в **административных задач** раздела.  
  
3.  Наведите указатель мыши **управление** в строке меню и нажмите кнопку **производные иерархии**.  
  
     ![Меню управления — выбрана производная иерархия](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "меню управления — выбрана производная иерархия")  
  
4.  Нажмите кнопку **Добавить производную иерархию (+)** на панели инструментов.  
  
     ![Добавьте кнопку производной иерархии](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "добавьте кнопку производной иерархии")  
  
5.  Тип **SuppliersInState** для **имя производной иерархии**.  
  
6.  Нажмите кнопку **Сохранить** на панели инструментов.  
  
     ![Сохранить производную иерархию кнопка](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "сохранить производную иерархию кнопки")  
  
7.  Перетащите **Supplier** из **доступные уровни: SuppliersInState** для **текущие уровни: SuppliersInState**.  
  
     ![Доступные сущности и иерархии для текущего уровня](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "доступные сущности и иерархии для текущего уровня")  
  
8.  Перетащите **состояние** из **доступные уровни: SuppliersInState** для **текущие уровни: SuppliersInState**. На экране должны соответствовать **текущие уровни** как показано на следующем рисунке.  
  
     ![Текущие уровни и предварительный просмотр производной иерархии](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "текущие уровни и предварительный просмотр производной иерархии")  
  
9. В **предварительного просмотра** окна, разверните **NY {Нью-Йорк}** и вы должны увидеть одного поставщика в этом состоянии, как показано на предыдущем рисунке.  
  
10. Переключитесь на главной странице **диспетчера основных данных** , щелкнув **SQL Server 2012 Master Data Services** в верхней части страницы.  
  
11. Нажмите кнопку **Браузер**.  
  
12. Наведите указатель мыши **иерархий** и нажмите кнопку **Derived: SuppliersInState**.  
  
     ![Иерархии - производные: SuppliersInState меню](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "иерархии - производные: SuppliersInState меню")  
  
13. Щелкните любой **состояние** узел в **представление в виде дерева** и вы увидите поставщики этого штата на правой панели.  
  
     ![Производная иерархия в обозревателе](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "производная иерархия в обозревателе")  
  
## <a name="next-step"></a>Следующий шаг  
 [Урок 5. Автоматизация очистки данных и сопоставления с помощью служб SSIS](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  