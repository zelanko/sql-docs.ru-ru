---
title: "Удаление столбца (табличные службы SSAS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 703db83b-e554-450e-813e-23ad08c1cdad
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e8b03c05cb27cdd2e736ad8bc57225408334827e
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="delete-a-column-ssas-tabular"></a>Удаление столбца (табличные службы SSAS)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]В этом разделе описывается удаление столбца из таблицы в табличной модели.  
  
## <a name="delete-a-model-table-column"></a>Удаление столбца таблицы модели  
  
> [!NOTE]  
>  При удалении столбца из таблицы модели этот столбец не удаляется из определения запроса секции. Если удаляемый столбец является частью секции, необходимо удалить его вручную из определения запроса секции. Несоблюдение требования по удалению столбца из определения запроса секции приведет к тому, что запросы к этому столбцу и возврат данных будут выполняться, но столбец не будет заполняться в таблице модели во время операций обработки. Дополнительные сведения см. в разделе [Секции (табличные службы SSAS)](../../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
#### <a name="to-delete-a-model-table-column"></a>Удаление столбца таблицы модели  
  
-   В конструкторе моделей в таблице, которая содержит удаляемый столбец, щелкните этот столбец правой кнопкой мыши и выберите команду **Удалить**.  
  
#### <a name="to-delete-a-model-table-column-by-using-the-table-properties-dialog-box"></a>Удаление столбца из таблицы модели с помощью диалогового окна «Свойства таблицы»  
  
1.  В конструкторе моделей щелкните таблицу, которая содержит удаляемый столбец, затем откройте меню **Таблица** и выберите пункт  **Свойства таблицы**.  
  
2.  В разделе **Имена столбцов из**выберите **Модель** (*чтобы использовать имена столбцов таблицы модели, если они отличаются от источника*).  
  
3.  В диалоговом окне **Изменение свойств таблицы** в окне предварительного просмотра таблицы снимите флажок, соответствующий удаляемому столбцу, после чего нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Добавление столбцов в таблицу (табличные службы SSAS)](../../analysis-services/tabular-models/add-columns-to-a-table-ssas-tabular.md)   
 [Секции (табличные службы SSAS)](../../analysis-services/tabular-models/partitions-ssas-tabular.md)  
  
  
