---
description: Сопоставление схожих данных (надстройка MDS для Excel)
title: Сопоставление схожих данных
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6fd6fc1-3569-42a5-b6cb-87a921c88f3b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 650c85f68003bda41e19e6f765898a23290480b6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "92255198"
---
# <a name="match-similar-data-mds-add-in-for-excel"></a>Сопоставление схожих данных (надстройка MDS для Excel)

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]воспользуйтесь возможностями служб Data Quality Services (DQS) для определения схожести данных.  
  
 Для этого можно:  
  
-   использовать базу знаний служб Data Quality Services по умолчанию или  
  
-   создать собственную пользовательскую базу знаний DQS и политику сопоставления. Дополнительные сведения см. в статье [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Необходимо иметь лист, содержащий данные, управляемые MDS. Дополнительные сведения см. в разделе [Экспорт данных в Excel из служб Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md).  
  
-   Необязательный элемент. Перед проверкой схожести можно объединить другие данные с данными, управляемыми MDS. Дополнительные сведения см. в разделе [Объединение данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/combine-data-mds-add-in-for-excel.md).  
  
### <a name="to-find-similarities-by-using-the-default-knowledge-base"></a>Поиск схожести с помощью базы знаний по умолчанию  
  
1.  На листе, который содержит данные, управляемые MDS, в группе **Качество данных** нажмите кнопку **Сопоставить данные**.  
  
2.  В диалоговом окне **Сопоставить данные** в списке **База знаний служб DQS** выберите пункт **Данные служб DQS (по умолчанию)**.  
  
3.  Для каждого столбца, содержащего данные, которые нужно сравнить, добавьте строку в диалоговом окне. Дополнительные сведения о полях в этом диалоговом окне см. в разделе [How to Set Matching Rule Parameters](../../data-quality-services/create-a-matching-policy.md#MatchingRules).  
  
4.  Когда сумма всех значений веса станет равна 100 %, нажмите кнопку **ОК**.  
  
### <a name="to-find-similarities-by-using-a-custom-knowledge-base"></a>Поиск схожести с помощью пользовательской базы знаний  
  
1.  На листе, который содержит данные, управляемые MDS, в группе **Качество данных** нажмите кнопку **Сопоставить данные**.  
  
2.  В списке **База знаний служб DQS** выберите имя пользовательской базы знаний.  
  
3.  Для каждого столбца на листе выберите домен служб DQS.  
  
4.  Когда все домены служб DQS будут сопоставлены со столбцами листа, нажмите кнопку **ОК**.  
  
## <a name="next-steps"></a>Next Steps  
  
-   Просмотрите дополнительные сведения для определения схожих данных. Дополнительные сведения см. в разделе [Столбцы сопоставления качества данных (службы DQS)](../../master-data-services/microsoft-excel-add-in/data-quality-matching-columns-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление качества данных в надстройка MDS для Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Сопоставление данных](../../data-quality-services/data-matching.md)  
  
  
