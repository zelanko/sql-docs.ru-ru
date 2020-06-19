---
title: Шаг 3. Проверка пакета, созданного на занятии 6 | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
author: janinezhang
ms.author: janinez
ms.openlocfilehash: c78ccd21b39cd882c037f44c0b37c5deb3bc06d8
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84951484"
---
# <a name="step-3-testing-the-lesson-6-package"></a>Шаг 3. Проверка пакета, созданного на занятии 6
  Во время выполнения пакет получит значение для свойства Directory из параметра VarFolderName.  
  
 Чтобы убедиться, что пакет обновляет свойство Directory новым значением во время выполнения, выполните пакет. Поскольку в новый каталог были скопированы только три файла образцов данных, поток данных будет запущен только три раза, а не 14 раз в соответствии с количеством файлов в исходном каталоге.  
  
## <a name="checking-the-package-layout"></a>Проверка макета пакета  
 Прежде чем тестировать пакет, следует убедиться, что поток управления и поток данных пакета, созданного на занятии 6, содержит объекты, показанные на следующих диаграммах. Поток управления должен быть таким же, как и поток управления в занятии 5. Поток данных должен быть идентичен потоку данных в занятии 5.  
  
 **Поток управления**  
  
 ![Поток управления](../../2014/tutorials/media/task3lesson6control.jpg "Поток управления")  
  
 **Поток данных**  
  
 ![Поток данных](../../2014/tutorials/media/task3lesson6data.jpg "Поток данных")  
  
### <a name="to-test-the-lesson-6-tutorial-package"></a>Тестирование пакета учебника Lesson 6  
  
1.  В меню Отладка выберите команду Начать отладку.  
  
2.  После окончания работы пакета выберите в меню Отладка пункт Остановить отладку.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Шаг 4. Развертывание пакета, созданного на занятии 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
