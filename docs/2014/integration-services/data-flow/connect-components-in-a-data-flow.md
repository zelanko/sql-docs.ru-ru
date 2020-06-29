---
title: Соединение компонентов в потоке данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eb04140fc5a065b93f8a08533b24ca786fc9202c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85432341"
---
# <a name="connect-components-in-a-data-flow"></a>Соединение компонентов в потоке данных
  Эта процедура описывает способ соединения выхода компонентов в потоке данных с другими компонентами того же потока.  
  
### <a name="to-connect-components-in-a-data-flow"></a>Соединение компонентов в потоке данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **Поток управления** , затем дважды щелкните задачу потока данных, содержащую поток данных, в котором требуется соединить компоненты.  
  
4.  В области конструктора на вкладке **Поток данных** выберите преобразование или источник, который необходимо соединить.  
  
5.  Перетащите зеленую стрелку выхода преобразования или источника на преобразование или целевой объект. Некоторые компоненты потока данных могут иметь вывод ошибок, который можно соединять аналогичным образом.  
  
    > [!NOTE]  
    >  Некоторые компоненты потока данных могут иметь несколько выходов; следовательно, можно подключить каждый выход к отдельному преобразованию или целевому объекту.  
  
6.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также  
 [Добавление или удаление компонента в потоке данных](data-flow.md)   
 [Настройка вывода ошибок в компоненте потока данных](../configure-an-error-output-in-a-data-flow-component.md)   
 [Поток данных](data-flow.md)  
  
  
