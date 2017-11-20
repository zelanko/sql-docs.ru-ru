---
title: "Преобразование столбца сведений диалоговое окно «» (мастер экспорта и импорта SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 985ba8a478999a153b3bb32649b98c3e809fc5e8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a>Диалоговое окно «Сведения о преобразовании столбца» (мастер импорта и экспорта SQL Server)
  Если дважды щелкнуть строку для отдельного столбца на странице **Просмотр сопоставления типов данных** , в мастере импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] откроется диалоговое окно **Сведения о преобразовании столбца** . На этой странице можно просмотреть подробные сведения о преобразовании отдельного столбца. Эта информация включает в себя следующие элементы.
-   Тип данных столбца на источник и назначение.
-   О преобразовании типов данных, мастер будет выполнять, если требуется преобразование.
-   Файлы сопоставления типов данных, используемые мастером для определения требуемого преобразования типа данных. 

## <a name="screen-shot-of-the-column-conversion-details-page"></a>Снимок экрана: страница "Сведения о преобразовании столбца" 
 На следующем снимке экрана показано диалоговое окно мастера **Сведения о преобразовании столбца** после того, как пользователь дважды щелкнул строку на странице **Просмотр сопоставления типов данных** . Еще раз взгляните на страницу **Просмотр сопоставления типов данных** и обратите внимание на [Просмотр сопоставления типов данных](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md).
 
В этом примере вы видите следующее.
-   `PersonID` Столбца в исходной таблице SQL Server имеет тип `int`. Мастер отображает этот тип для SQL Server Integration Services (SSIS) `DT_I4` тип данных, который является 4 байтовое целое число со знаком, ссылаясь на файл сопоставления типов данных MSSQLToSSIS10.xml.
-   `PersonID` Столбец в целевой таблице SQL Server также имеет тип `int`. Мастер сопоставляет этот тип в один и тот же тип данных служб SSIS.
-   Заключительный шаг мастера, *этот столбец не нужно преобразовывать*.
 
  
 ![Страница мастера импорта и экспорта преобразование столбца](../../integration-services/import-export-data/media/column-conversion.png "страницу преобразование столбца из мастера импорта и экспорта") 
  
## <a name="whats-next"></a>Дальнейшие действия  
 После просмотра сведений о преобразовании столбца и нажатия кнопки **ОК**диалоговое окно **Сведения о преобразовании столбца** вернет вас на страницу **Просмотр сопоставления типов данных** . Дополнительные сведения см. в разделе [Просмотр сопоставления типов данных](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md).  

## <a name="see-also"></a>См. также:
[Сопоставление типов данных в мастере импорта и экспорта SQL Server](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)

