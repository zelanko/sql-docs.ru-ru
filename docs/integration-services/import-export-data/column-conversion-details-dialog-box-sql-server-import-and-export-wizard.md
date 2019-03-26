---
title: Диалоговое окно "Сведения о преобразовании столбца" (мастер импорта и экспорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 02/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ac4a69a7aca5a1e354e345a47e23b413fc9d3422
ms.sourcegitcommit: 5683044d87f16200888eda2c2c4dee38ff87793f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58221918"
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a>Диалоговое окно «Сведения о преобразовании столбца» (мастер импорта и экспорта SQL Server)
  Если дважды щелкнуть строку для отдельного столбца на странице **Просмотр сопоставления типов данных** , в мастере импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] откроется диалоговое окно **Сведения о преобразовании столбца** . На этой странице можно просмотреть подробные сведения о преобразовании отдельного столбца. Эта информация включает в себя следующие элементы.
-   Тип данных столбца в источнике и назначении.
-   Преобразование типа данных, которое будет выполнено мастером (если преобразование требуется).
-   Файлы сопоставления типов данных, используемые мастером для определения требуемого преобразования типа данных. 

## <a name="screen-shot-of-the-column-conversion-details-page"></a>Снимок экрана: страница "Сведения о преобразовании столбца" 
 На следующем снимке экрана показано диалоговое окно мастера **Сведения о преобразовании столбца** после того, как пользователь дважды щелкнул строку на странице **Просмотр сопоставления типов данных** . Еще раз взгляните на страницу **Просмотр сопоставления типов данных** и обратите внимание на [Просмотр сопоставления типов данных](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md).
 
В этом примере вы видите следующее.
-   Столбец `PersonID` в таблице источника SQL Server имеет тип `int`. Мастер сопоставляет этот тип с типом данных SQL Server Integration Services (SSIS) `DT_I4`, который представляет собой четырехбайтовое целое число со знаком, задавая ссылку на файл сопоставления типов данных MSSQLToSSIS10.xml.
-   Столбце `PersonID` в таблице назначения SQL Server также имеет тип `int`. Мастер сопоставляет этот тип с тем же типом данных служб SSI.
-   Мастер выдает заключение *Этот столбец не нужно преобразовывать*.
 
  
 ![Страница "Преобразование столбца" в мастере импорта и экспорта](../../integration-services/import-export-data/media/column-conversion.png "Страница \"Преобразование столбца\" в мастере импорта и экспорта") 
  
## <a name="whats-next"></a>Дальнейшие действия  
 После просмотра сведений о преобразовании столбца и нажатия кнопки **ОК**диалоговое окно **Сведения о преобразовании столбца** вернет вас на страницу **Просмотр сопоставления типов данных** . Дополнительные сведения см. в разделе [Просмотр сопоставления типов данных](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md).  

## <a name="see-also"></a>См. также раздел
[Сопоставление типов данных в мастере импорта и экспорта SQL Server](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)
