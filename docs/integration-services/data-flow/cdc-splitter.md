---
title: "Разделитель CDC | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.designer.cdcsplitter.f1
ms.assetid: 167bc5c6-fa36-439d-987c-b20acd1a77e2
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0e2bee6609acacd6c9d441eae62d178818aea27a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="cdc-splitter"></a>Разделитель CDC
  Разделитель CDC разбивает один поток строк изменений из потока исходных данных CDC на различные потоки данных, относящиеся к операциям Insert, Update и Delete. Разбиение потока данных осуществляется на основе обязательного столбца `__$operation` и его стандартных значений в таблицах изменений [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
|Значение операции|Вывод|Description|  
|------------------------|------------|-----------------|  
|1|Delete|Удаленная строка|  
|2|Insert|Вставленная строка (недоступно при использовании режима CDC **Суммарные со слиянием** )|  
|3|Update|Строка перед обновлением (доступно только при использовании режима CDC **Все со старыми значениями** )|  
|4|Update|Строка после обновления (следует за строкой, которая имела место перед обновлением)|  
|5|Update|Строка слияния (доступно только при использовании режима CDC **Суммарные со слиянием** )|  
|Другое|Ошибка||  
  
 Разделитель вы можете использовать для подключения к стандартным выводам INSERT, DELETE и UPDATE в целях дальнейшей обработки.  
  
 Преобразование «Разделитель CDC» имеет один обычный ввод и один вывод ошибок.  
  
## <a name="error-handling"></a>Обработка ошибок  
 Преобразование «Разделитель CDC» имеет вывод ошибок. Входные строки с недопустимым значением в столбце $operation рассматриваются как ошибочные и обрабатываются в соответствии со свойством ввода **ErrorRowDisposition** .  
  
 Вывод ошибок компонента включает следующие выходные столбцы.  
  
-   **Код ошибки**. Задан равным 1.  
  
-   **Столбец с ошибкой**. Входной столбец, вызывающий ошибку (это относится к ошибкам преобразования).  
  
-   **Столбцы строки с ошибкой**. Входные столбцы строки, которая вызвала ошибку.  
  
## <a name="configuring-the-cdc-splitter"></a>Настройка разделителя CDC  
 Какие-либо настраиваемые свойства для разделителя CDC отсутствуют.  
  
 Дополнительные сведения об использовании разделителя CDC см. в разделе «Компоненты CDC для служб Microsoft SQL Server Integration Services».  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые могут быть заданы программным путем.  
  
 Открытие диалогового окна **Расширенный редактор** .  
  
-   На экране **Поток данных** вашего проекта [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] щелкните правой кнопкой мыши разделитель CDC и выберите элемент **Показать расширенный редактор**.  
  
## <a name="see-also"></a>См. также  
 [Направления потока CDC в соответствии с типом изменения](../../integration-services/data-flow/direct-the-cdc-stream-according-to-the-type-of-change.md)  
  
  

