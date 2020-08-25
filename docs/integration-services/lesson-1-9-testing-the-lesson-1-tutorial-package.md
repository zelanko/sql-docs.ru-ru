---
description: Шаг 9. Тестирование учебного пакета занятия 1
title: Шаг 9. Проверка учебного пакета, созданного на занятии 1 | Документация Майкрософт
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 758f5e0c312afc2a8310743f917cc00a1c43462c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88462016"
---
# <a name="lesson-1-9-test-the-lesson-1-package"></a>Занятие 1-9. Тестирование пакета занятия 1

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



В этом учебнике были выполнены следующие задачи:  
  
-   Был создан проект служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
-   Были настроены диспетчеры подключений для пакета для подключения к исходным и целевым данным.  
  
-   Был добавлен поток данных, который получает данные от источника «неструктурированный файл», производит необходимые преобразования «Уточняющий запрос» и настраивает данные для назначения.  
  
Пакет создан и готов к тестированию.
  
## <a name="check-the-package-components"></a>Проверка компонентов пакета
  
Прежде чем проверить пакет, нужно убедиться в том, что потоки данных и управления в пакете занятия 1 содержат объекты, показанные на следующих диаграммах.  
  
**Поток управления** 
  
![Поток управления в пакете](../integration-services/media/task9lesson1control.gif "Поток управления в пакете")  
  
**Поток данных**  
  
![Поток данных в пакете](../integration-services/media/task9lesson1data.gif "Поток данных в пакете")  
  
## <a name="run-the-lesson-1-package"></a>Выполнение учебного пакета занятия 1  
  
1.  В меню **Отладка** выберите пункт **Начать отладку**.  
  
    Пакет запускается, и в таблицу фактов **NewFactCurrencyRate** из базы данных **AdventureWorksDW2012** добавляется 1097 строк. Чтобы проверить этот результат, перейдите на вкладку **Поток данных**.
  
2.  После окончания работы пакета выберите в меню **Отладка** пункт **Остановить отладку**.  
  
## <a name="go-to-next-lesson"></a>Переход к следующему занятию
[Занятие 2. Добавление циклов с помощью служб SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a>См. также  
[Запуск проектов и пакетов](packages/run-integration-services-ssis-packages.md) 
  
  
  
