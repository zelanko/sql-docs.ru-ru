---
title: "Шаг 3. Проверка пакета, созданного на занятии 6 | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d3127ba4edc47aa7ae9b6aab8fc309fe2c854da3
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="lesson-6-3---testing-the-lesson-6-package"></a>Занятие 6–3. Проверка пакета, созданного на занятии 6
Во время выполнения пакет получит значение для свойства Directory из параметра VarFolderName.  
  
Чтобы убедиться, что пакет обновляет свойство Directory новым значением во время выполнения, выполните пакет. Поскольку в новый каталог были скопированы только три файла образцов данных, поток данных будет запущен только три раза, а не 14 раз в соответствии с количеством файлов в исходном каталоге.  
  
## <a name="checking-the-package-layout"></a>Проверка макета пакета  
Прежде чем тестировать пакет, следует убедиться, что поток управления и поток данных пакета, созданного на занятии 6, содержит объекты, показанные на следующих диаграммах. Поток управления должен быть таким же, как и поток управления в занятии 5. Поток данных должен быть идентичен потоку данных в занятии 5.  
  
**Поток управления**  
  
![Поток управления](../integration-services/media/task3lesson6control.jpg "Поток управления")  
  
**Поток данных**  
  
![Поток данных](../integration-services/media/task3lesson6data.jpg "Поток данных")  
  
### <a name="to-test-the-lesson-6-tutorial-package"></a>Тестирование пакета учебника Lesson 6  
  
1.  В меню Отладка выберите команду Начать отладку.  
  
2.  После окончания работы пакета выберите в меню Отладка пункт Остановить отладку.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Шаг 4. Развертывание пакета, созданного на занятии 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
  
