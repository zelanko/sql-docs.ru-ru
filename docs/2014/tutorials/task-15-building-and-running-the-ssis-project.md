---
title: 'Задача 15: Построение и запуск проекта служб SSIS | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 13adf4e0-216a-4992-b13d-b7b1e1629e77
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 844114cf513cf207aaefa2aa747d861c74368b80
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249454"
---
# <a name="task-15-building-and-running-the-ssis-project"></a>Задача 15. Построение и запуск проекта служб SSIS
  В этой задаче вы создадите и выполните проект служб SSIS. При наличии 64-разрядной версии Excel 2010, установленной на компьютере, следует задать значение **Run64BitRuntime** для **False** для источника "Excel" для работы.  
  
1.  В **обозревателе решений** окно, нажмите кнопку **проекта** на меню и выберите **свойства CleanseAndCurateSuppliers**.  
  
2.  В **свойства** диалогового окна разверните узел **свойства конфигурации** слева, а затем нажмите **Отладка**.  
  
3.  Задайте **Run64BitRuntime** для **False**.  
  
     ![Свойства проекта CleanseAndCurateSuppliers](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "свойства проекта CleanseAndCurateSuppliers")  
  
4.  Нажмите кнопку **ОК** закрыть **свойства** диалоговое окно.  
  
5.  Нажмите кнопку **построения** в строке меню щелкните **построение CleanseAndCurateSuppliers**. Убедитесь, что при построении не было ошибок.  
  
6.  Нажмите кнопку **Отладка** в строке меню щелкните **начать отладку**.  
  
7.  Просмотрите сообщения в **ход выполнения** окна и убедитесь, что выполнение пакета завершено успешно.  
  
     ![Полученный в результате окно хода выполнения](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "результаты из окна хода выполнения")  
  
     ![Конечное состояние из окна хода выполнения](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "Окончательное состояние из окна хода выполнения")  
  
8.  Нажмите кнопку **Отладка** в строке меню щелкните **остановить отладку** остановить сеанс отладки. Если пакет вызывает ошибку, необходимо включить средства просмотра данных и посмотреть на потоки данных между компонентами.  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 16. Проверка с помощью диспетчера основных данных](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  
