---
title: Задача 15. сборка и запуск проекта служб SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 13adf4e0-216a-4992-b13d-b7b1e1629e77
ms.author: lle
author: lrtoyou1223
ms.openlocfilehash: 50b313f63ae434a96d6c0e38f3c8b600914c806d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66822992"
---
# <a name="task-15-building-and-running-the-ssis-project"></a>Задача 15. Построение и запуск проекта служб SSIS

  В этой задаче вы создадите и выполните проект служб SSIS. Если на компьютере установлена 64-разрядная версия Excel 2010, следует присвоить параметру **Run64BitRuntime** значение **false** , чтобы источник Excel работал.  
  
1.  В окне **Обозреватель решений** в меню выберите пункт **проект** и щелкните **Свойства CleanseAndCurateSuppliers**.  
  
2.  В диалоговом окне **Свойства** разверните узел **Свойства конфигурации** слева и нажмите кнопку **Отладка**.  
  
3.  Задайте **** для Run64BitRuntime **значение false**.  
  
     ![Свойства проекта CleanseAndCurateSuppliers](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "Свойства проекта CleanseAndCurateSuppliers")  
  
4.  Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **свойства** .  
  
5.  Щелкните **Сборка** в строке меню и выберите **Сборка CleanseAndCurateSuppliers**. Убедитесь, что при построении не было ошибок.  
  
6.  Щелкните **Отладка** в строке меню и выберите **начать отладку**.  
  
7.  Проверьте сообщения в окне **ход выполнения** и убедитесь, что пакет успешно выполнен и завершил работу.  
  
     ![Результаты из окна хода выполнения](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "Результаты из окна хода выполнения")  
  
     ![Окончательное состояние из окна хода выполнения](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "Окончательное состояние из окна хода выполнения")  
  
8.  Щелкните **Отладка** в строке меню и нажмите кнопку " **Отключить отладку** ", чтобы отключить сеанс отладки. Если пакет вызывает ошибку, необходимо включить средства просмотра данных и посмотреть на потоки данных между компонентами.  
  
## <a name="next-step"></a>Дальнейшее действие  
 [Задача 16. Проверка с помощью диспетчера основных данных](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  
