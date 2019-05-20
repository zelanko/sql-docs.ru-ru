---
title: Шаг 3. Тестирование пакета, созданного на занятии 6 | Документация Майкрософт
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 001ba5fc56393cbbcdbc8b5379abc8390dc05e0a
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65721240"
---
# <a name="lesson-6-3-test-the-lesson-6-package"></a>Занятие 6-3. Тестирование пакета занятия 6

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Во время выполнения пакет получает значение для свойства **Каталог** из параметра **VarFolderName**.  
  
Чтобы убедиться в том, что пакет обновляет свойство **Каталог**, выполните пакет. Так как в новый каталог были скопированы три файла образцов данных, поток данных запускается три раза.
  
## <a name="check-the-package-layout"></a>Проверка макета пакета  
Прежде чем проверить пакет, нужно убедиться в том, что потоки данных и управления в пакете занятия 6 аналогичны объектам, показанным на следующих схемах:   
  
**Поток управления**  
  
![Поток управления](../integration-services/media/task4lesson2control.gif "Поток управления")  
  
**Поток данных**  
  
![Поток данных](../integration-services/media/task5lesson5data.gif "Поток данных")  
  
## <a name="test-the-lesson-6-package"></a>Тестирование пакета занятия 6  
  
1.  В меню **Отладка** выберите команду **Начать отладку**.  
  
2.  После окончания работы пакета выберите в меню **Отладка** пункт **Остановить отладку**.  
  
## <a name="go-to-next-task"></a>Переход к следующей задаче
[Шаг 4. Развертывание пакета занятия 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
  
