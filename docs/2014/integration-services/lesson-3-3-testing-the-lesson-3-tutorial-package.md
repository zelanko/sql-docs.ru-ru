---
title: Шаг 3. Проверка учебного пакета, созданного на занятии 3 | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 690c7a670ca448c14c984b9fda76098ae7269c4a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37322714"
---
# <a name="step-3-testing-the-lesson-3-tutorial-package"></a>Шаг 3. Проверка учебного пакета, созданного на занятии 3
  В этой задаче вы выполните пакет Lesson 3.dtsx. После запуска пакета в окне «Журнал событий» отображаются записи, которые заносятся в файл журнала. После завершения выполнения пакета следует проверить, что регистратор сформировал содержимое файла журнала.  
  
## <a name="checking-the-package-layout"></a>Проверка макета пакета  
 Прежде чем проверить пакет, нужно убедиться в том, что потоки данных и управления в пакете занятия 3 содержат объекты, показанные на следующих  диаграммах. Поток управления должен быть таким же, как и поток управления в занятии 2. Поток данных должен быть идентичен потоку данных в занятиях 1 и 2.  
  
 **Поток управления**  
  
 ![Поток управления в пакете](../../2014/tutorials/media/task4lesson2control.gif "Поток управления в пакете")  
  
 **Поток данных**  
  
 ![Поток данных в пакете](../../2014/tutorials/media/task9lesson1data.gif "Поток данных в пакете")  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a>Выполнение учебного пакета занятия 4  
  
1.  В меню «Службы SSIS» выберите «Регистрация событий».  
  
2.  В меню **Отладка** выберите пункт **Запустить отладку**.  
  
3.  После окончания работы пакета выберите в меню **Отладка** пункт **Остановить отладку**.  
  
### <a name="to-examine-the-generated-log-file"></a>Изучение созданного файла журнала  
  
-   В приложении «Блокнот» или другом текстовом редакторе откройте файл TutorialLog.log.  
  
-   Хотя семантика сведений созданный для `PipelineExecutionPlan` и `PipelineExecutionTrees` событий выходят за рамки данного руководства, вы увидите, что в первой строке перечислены поля сведений, указанных в **сведения** вкладке **Настройка журналов служб SSIS** диалоговое окно. Кроме того, можно проверить, что два выбранных события (PipelineExecutionPlan и PipelineExecutionTrees) были занесены в журнал для каждой итерации цикла ForEach.  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Занятие 4. Добавление перенаправления потока ошибок](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  
