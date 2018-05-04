---
title: Удаление столбца | Документы Microsoft
ms.custom: ''
ms.date: 02/22/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 703db83b-e554-450e-813e-23ad08c1cdad
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: baa5527f9c7eef1a2c6099dfb423347117a1f41d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
  
