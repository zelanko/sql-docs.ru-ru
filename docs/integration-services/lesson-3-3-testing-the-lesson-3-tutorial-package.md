---
title: "Шаг 3: Проверка учебного пакета занятия 3 | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d6477267c95ffd200f70b2c93191dfaf0883a4af
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-3-3---testing-the-lesson-3-tutorial-package"></a>Занятие 3-3-Проверка учебного пакета занятия 3
В этой задаче вы выполните пакет Lesson 3.dtsx. После запуска пакета в окне «Журнал событий» отображаются записи, которые заносятся в файл журнала. После завершения выполнения пакета следует проверить, что регистратор сформировал содержимое файла журнала.  
  
## <a name="checking-the-package-layout"></a>Проверка макета пакета  
Прежде чем проверить пакет, нужно убедиться в том, что потоки данных и управления в пакете занятия 3 содержат объекты, показанные на следующих  диаграммах. Поток управления должен быть таким же, как и поток управления в занятии 2. Поток данных должен быть идентичен потоку данных в занятиях 1 и 2.  
  
**Поток управления**  
  
![Поток в пакете управления](../integration-services/media/task4lesson2control.gif "поток в пакете управления")  
  
**Поток данных**  
  
![Поток данных в пакете](../integration-services/media/task9lesson1data.gif "потока данных в пакете")  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a>Выполнение учебного пакета занятия 4  
  
1.  В меню «Службы SSIS» выберите «Регистрация событий».  
  
2.  В меню **Отладка** выберите пункт **Запустить отладку**.  
  
3.  После окончания работы пакета выберите в меню **Отладка** пункт **Остановить отладку**.  
  
### <a name="to-examine-the-generated-log-file"></a>Изучение созданного файла журнала  
  
-   В приложении «Блокнот» или другом текстовом редакторе откройте файл TutorialLog.log.  
  
-   Хотя семантика сведений, созданных для событий **PipelineExecutionPlan** и **PipelineExecutionTrees** , не входит в список тем данного учебника, следует обратить внимание на то, что в первой строке перечислены поля сведений, указанных на вкладке **Подробности** диалогового окна **Настройка журналов служб SSIS** . Кроме того, можно проверить, что два выбранных события (PipelineExecutionPlan и PipelineExecutionTrees) были занесены в журнал для каждой итерации цикла ForEach.  
  
## <a name="next-lesson"></a>Следующее занятие  
[Занятие 4. Добавление перенаправления потока ошибок с помощью служб SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  
  

