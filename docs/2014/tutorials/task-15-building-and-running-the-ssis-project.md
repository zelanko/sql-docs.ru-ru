---
title: 'Задача 15: Построение и запуск проекта служб SSIS | Документы Microsoft'
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
ms.topic: article
ms.assetid: 13adf4e0-216a-4992-b13d-b7b1e1629e77
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9a63fcf03591626d5b4c1351d5ce868ef7a9fb65
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100320"
---
# <a name="task-15-building-and-running-the-ssis-project"></a>Задача 15. Построение и запуск проекта служб SSIS
  В этой задаче вы создадите и выполните проект служб SSIS. При наличии 64-разрядной версии Excel 2010, установленной на компьютере, следует задать значение **Run64BitRuntime** для **False** источника Excel для работы.  
  
1.  В **обозревателе решений** окно, нажмите кнопку **проекта** на меню и выберите пункт **свойства CleanseAndCurateSuppliers**.  
  
2.  В **свойства** диалогового окна разверните **свойства конфигурации** слева, а затем нажмите **Отладка**.  
  
3.  Задать **Run64BitRuntime** для **False**.  
  
     ![Свойства проекта CleanseAndCurateSuppliers](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "свойства проекта CleanseAndCurateSuppliers")  
  
4.  Нажмите кнопку **ОК** закрыть **свойства** диалоговое окно.  
  
5.  Нажмите кнопку **построения** в строке меню щелкните **построение CleanseAndCurateSuppliers**. Убедитесь, что при построении не было ошибок.  
  
6.  Нажмите кнопку **отладки** в строке меню щелкните **начать отладку**.  
  
7.  Просмотрите сообщения в **выполняется** окна и убедитесь, что выполнение пакета завершено успешно.  
  
     ![Результаты из окна хода выполнения](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "результатов из окна хода выполнения")  
  
     ![Окончательное состояние из окна хода выполнения](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "Окончательное состояние из окна хода выполнения")  
  
8.  Нажмите кнопку **отладки** в строке меню щелкните **остановить отладку** для остановки сеанса отладки. Если пакет вызывает ошибку, необходимо включить средства просмотра данных и посмотреть на потоки данных между компонентами.  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 16. Проверка с помощью диспетчера основных данных](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  