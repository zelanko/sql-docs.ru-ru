---
title: Шаг 9. Проверка учебного пакета, созданного на занятии 1 | Документация Майкрософт
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dde0ffe53ab5763230cafa752d687ab42d3a60c5
ms.sourcegitcommit: dd794633466b1da8ead9889f5e633bdf4b3389cd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54143224"
---
# <a name="lesson-1-9-test-the-lesson-1-package"></a>Занятие 1-9. Тестирование пакета занятия 1

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
  
1.  В меню **Отладка** выберите команду **Начать отладку**.  
  
    Пакет запускается, и в таблицу фактов **NewFactCurrencyRate** из базы данных **AdventureWorksDW2012** добавляется 1097 строк. Чтобы проверить этот результат, перейдите на вкладку **Поток данных**.
  
2.  После окончания работы пакета выберите в меню **Отладка** пункт **Остановить отладку**.  
  
## <a name="go-to-next-lesson"></a>Переход к следующему занятию
[Занятие 2. Добавление циклов с помощью служб SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a>См. также раздел  
[Запуск проектов и пакетов](packages/run-integration-services-ssis-packages.md) 
  
  
  
