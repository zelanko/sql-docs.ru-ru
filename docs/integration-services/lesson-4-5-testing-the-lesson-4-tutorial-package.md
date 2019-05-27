---
title: Шаг 5. Проверка учебного пакета, созданного на занятии 4 | Документация Майкрософт
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 5f18df92-0248-4858-836b-c8b02f0e0439
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f1c7ec3026050181ae31150c4b5e190a65d889d4
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65721511"
---
# <a name="lesson-4-5-test-the-lesson-4-package"></a>Занятие 4-5. Тестирование пакета занятия 4

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



На стадии выполнения происходит ошибка поиска соответствия при работе преобразования "Поиск ключа валюты" в поврежденном файле **Currency_BAD.txt**. Так как вывод ошибок преобразования "Поиск ключа валюты" настроен для перенаправления строк новому адресату "Неудачные обращения", операция не завершается ошибкой, и пакет успешно выполняется. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] записывает все ошибочные строки в файл **ErrorOutput.txt**.  
  
В этой задаче требуется проверить измененную конфигурацию вывода ошибок, запустив пакет на выполнение. После успешного выполнения пакета проверьте содержимое файла **ErrorOutput.txt**.  
  
> [!NOTE]  
> Если нет необходимости накапливать ошибочные строки в файле **ErrorOutput.txt**, вручную очистите содержимое файла между выполнениями пакета.  
  
## <a name="check-the-package-layout"></a>Проверка макета пакета  
Перед проверкой пакета убедитесь в том, что поток управления и поток данных в пакете занятия 4 аналогичны представленным на следующих схемах: 
  
**Поток управления**  
  
![Поток управления в пакете](../integration-services/media/task4lesson2control.gif "Поток управления в пакете")  
  
**Поток данных**  
  
![Поток данных в пакете](../integration-services/media/task5lesson5data.gif "Поток данных в пакете")  
  
## <a name="run-the-lesson-4-tutorial-package"></a>Выполнение учебного пакета занятия 4  
  
1.  В меню **Отладка** выберите команду **Начать отладку**.  
  
2.  После окончания работы пакета выберите в меню **Отладка** пункт **Остановить отладку**.  
  
## <a name="view-the-contents-of-the-erroroutputtxt-file"></a>Просмотр содержимого файла ErrorOutput.txt  
  
Откройте файл **ErrorOutput.txt** в Блокноте или другом текстовом редакторе. Порядок столбцов по умолчанию: AverageRate, CurrencyID, CurrencyDate, EndOfDateRate, ErrorCode, ErrorColumn, ErrorDescription.  
 
Все строки в файле содержат несовпадающие значения в столбце CurrencyID — BAD, в столбце ErrorCode — -1 071 607 778, в столбце ErrorColumn — 0 и в столбце ErrorDescription — "В результате уточняющего запроса для строки не обнаружено соответствия". Значение столбца ErrorColumn равно 0, так как ошибка не является специфической для данного столбца. Вместо этого происходит сбой операции поиска.
  
  
## <a name="next-lesson"></a>Следующее занятие
[Занятие 5. Добавление конфигураций пакетов SSIS в модель развертывания пакетов](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
