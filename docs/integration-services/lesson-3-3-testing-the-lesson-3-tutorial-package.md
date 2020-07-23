---
title: Шаг 3. Проверка учебного пакета, созданного на занятии 3 | Документация Майкрософт
ms.custom: ''
ms.date: 01/04/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b8a159e1f1e70fefed181f6f47715201731b63dc
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922202"
---
# <a name="lesson-3-3-test-the-lesson-3-tutorial-package"></a>Занятие 3-3. Тестирование учебного пакета занятия 3

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



В этой задаче вы выполните пакет **Lesson 3.dtsx**. После запуска пакета в окне **Журнал событий** отображаются записи, которые SSIS заносит в файл журнала с помощью регистратора. После завершения выполнения пакета можно просмотреть содержимое файла журнала.  
  
## <a name="check-the-package-layout"></a>Проверка макета пакета  
Прежде чем проверить пакет, нужно убедиться в том, что потоки данных и управления в пакете занятия 3 похожи на объекты, показанные на следующих диаграммах. Поток управления должен быть таким же, как в занятии 2, а поток данных должен быть таким же, как в занятиях 1 и 2.  
  
**Поток управления**  
  
![Поток управления в пакете](../integration-services/media/task4lesson2control.gif "Поток управления в пакете")  
  
**Поток данных**  
  
![Поток данных в пакете](../integration-services/media/task9lesson1data.gif "Поток данных в пакете")  
  
## <a name="run-the-lesson-3-tutorial-package"></a>Выполнение учебного пакета занятия 3  
  
1.  В меню SSIS выберите **События журнала**.  
  
2.  В меню **Отладка** выберите команду **Начать отладку**.  
  
3.  После окончания работы пакета выберите в меню **Отладка** пункт **Остановить отладку**.  
  
## <a name="examine-the-generated-log-file"></a>Изучение созданного файла журнала  
  
-   В приложении «Блокнот» или другом текстовом редакторе откройте файл TutorialLog.log.  
  
-   Полное описание информации, создаваемой для событий **PipelineExecutionPlan** и **PipelineExecutionTrees**, выходит за рамки данного руководства.  В файле журнала можно заметить, что в первой строке перечислены поля сведений, указанные на вкладке **Подробности** диалогового окна **Настройка журналов служб SSIS**. Вы также можете видеть, что службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] занесли в журнал два выбранных события (**PipelineExecutionPlan** и **PipelineExecutionTrees**) для каждой итерации цикла Foreach.  
  
## <a name="next-lesson"></a>Следующее занятие  
[Занятие 4. Добавление перенаправления потока ошибок с помощью служб SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  
  
