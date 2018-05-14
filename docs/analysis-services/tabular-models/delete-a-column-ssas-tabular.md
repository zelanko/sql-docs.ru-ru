---
title: Удаление столбца | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e850740754fea16aa82c60b3abda9f86bafeaff
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="delete-a-column"></a>Удаление столбца 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  В этой статье описывается удаление столбца из таблицы в табличной модели.  
  
## <a name="delete-a-model-table-column"></a>Удаление столбца таблицы модели  
  
> [!NOTE]  
>  При удалении столбца из таблицы модели этот столбец не удаляется из определения запроса секции. Если удаляемый столбец является частью секции, необходимо удалить его вручную из определения запроса секции. Несоблюдение требования по удалению столбца из определения запроса секции приведет к тому, что запросы к этому столбцу и возврат данных будут выполняться, но столбец не будет заполняться в таблице модели во время операций обработки. Дополнительные сведения см. в разделе [секций](../../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
#### <a name="to-delete-a-model-table-column"></a>Удаление столбца таблицы модели  
  
-   В конструкторе моделей в таблице, которая содержит удаляемый столбец, щелкните этот столбец правой кнопкой мыши и выберите команду **Удалить**.  
  
#### <a name="to-delete-a-model-table-column-by-using-the-table-properties-dialog-box"></a>Удаление столбца из таблицы модели с помощью диалогового окна «Свойства таблицы»  
  
1.  В конструкторе моделей щелкните таблицу, которая содержит удаляемый столбец, затем откройте меню **Таблица** и выберите пункт  **Свойства таблицы**.  
  
2.  В разделе **Имена столбцов из**выберите **Модель** (*чтобы использовать имена столбцов таблицы модели, если они отличаются от источника*).  
  
3.  В диалоговом окне **Изменение свойств таблицы** в окне предварительного просмотра таблицы снимите флажок, соответствующий удаляемому столбцу, после чего нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Добавление столбцов в таблицу](../../analysis-services/tabular-models/add-columns-to-a-table-ssas-tabular.md)   
 [Секции](../../analysis-services/tabular-models/partitions-ssas-tabular.md)  
  
  
