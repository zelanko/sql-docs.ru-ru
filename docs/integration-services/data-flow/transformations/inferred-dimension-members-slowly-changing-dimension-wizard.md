---
title: "Выводимых элементов измерения (мастер медленно изменяющихся измерений) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b99116c19f5ec69fcf382069a1ca3c76ee65b3d6
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a>Выводимые элементы измерения (мастер медленно изменяющихся измерений)
  Диалоговое окно **Выводимые элементы измерения** используется для задания параметров их вывода. Выводимые элементы существуют в случае, когда таблица фактов ссылается на еще не загруженные элементы таблицы измерения. При загрузке данных для выводимого элемента можно просто обновить существующую запись, а не создавать ее заново.  
  
 Дополнительные сведения о работе этого мастера см. в разделе [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Включить поддержку выводимых элементов измерения**  
 В случае включения выводимых элементов, необходимо выбрать один из двух следующих параметров.  
  
 **Все столбцы с типом изменения имеют значение NULL**  
 Позволяет указать, вводить ли значения NULL во все столбцы с типом изменения в новой записи выводимых элементов.  
  
 **Использовать логический столбец для указания принадлежности текущей записи к выводимым элементам**  
 Позволяет задать, использовать ли существующий логический столбец для указания, является ли текущая запись выводимым элементом.  
  
 **Признак выводимого элемента**  
 Если выбрано использовать логический столбец для указания выводимых элементов как описано выше, выберите столбец из списка.  
  
## <a name="see-also"></a>См. также раздел  
 [Настройка выходов при помощи мастера медленно меняющихся измерений](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  

