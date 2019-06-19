---
title: Разбиение набора данных с помощью преобразования "Условное разбиение" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Conditional Split transformation
- splitting dataset
- datasets [Integration Services], splitting
ms.assetid: 23b3e84f-9296-4dc9-81c0-c7f06ae3f1ff
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8c84a35ea40187cc2b40ab9e60d75bb0c9b62620
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65725823"
---
# <a name="split-a-dataset-by-using-the-conditional-split-transformation"></a>Разбиение набора данных с помощью преобразования «Условное разбиение»

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Чтобы добавить и настроить преобразование «Условное разбиение», пакет должен содержать по крайней мере одну задачу потока данных и один источник.  
  
### <a name="to-conditionally-split-a-dataset"></a>Чтобы условно разбить набор данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **Поток данных** и перенесите преобразование «Условное разбиение» из окна **Область элементов**в область конструктора.  
  
4.  Подключите преобразование «Условное разбиение» к потоку данных, перетащив соединитель из источника данных или предыдущего преобразования в преобразование «Условное разбиение».  
  
5.  Дважды щелкните преобразование «Условное разбиение».  
  
6.  В окне **Редактор преобразования «Условное разбиение»** постройте выражения для использования в качестве условий, перетащив необходимые переменные, столбцы, функции и операторы в столбец **Условие** сетки. Можно также ввести выражение в столбец **Условие** .  
  
    > [!NOTE]  
    >  Переменная или столбец могут быть использованы в нескольких выражениях.  
  
    > [!NOTE]  
    >  Если выражение недопустимо, его текст выделяется, а в подсказке к столбцу появляется описание ошибки.  
  
7.  При необходимости измените значения в столбце **Имя выхода** . Имена по умолчанию — «Case 1», «Case 2» и т. д.  
  
8.  Для изменения последовательности оценки условий нажмите кнопку со стрелкой вверх или вниз.  
  
    > [!NOTE]  
    >  Поместите условия, которые будут выполняться чаще всего, в начало списка.  
  
9. Можно изменить имя выхода по умолчанию для строк данных, которые не подходят ни под одно из условий.  
  
10. Для настройки вывода ошибок нажмите **Настроить вывод ошибок**. Дополнительные сведения см. в статье [Отладка потока данных](../../../integration-services/troubleshooting/debugging-data-flow.md).  
  
11. Нажмите кнопку **ОК**.  
  
12. Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также:  
 [Conditional Split Transformation](../../../integration-services/data-flow/transformations/conditional-split-transformation.md)   
 [Преобразования служб Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Пути служб Integration Services](../../../integration-services/data-flow/integration-services-paths.md)   
 [Типы данных служб Integration Services](../../../integration-services/data-flow/integration-services-data-types.md)   
 [Задача потока данных](../../../integration-services/control-flow/data-flow-task.md)   
 [Выражения служб Integration Services (SSIS)](../../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  
